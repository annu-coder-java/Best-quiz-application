import javax.swing.*;
import java.awt.*;
import java.awt.event.*;





class Q implements ActionListener
{

JFrame f;
JLabel l1;
JButton javaBtn,htmlBtn,cssBtn,nextBtn,homeBtn,restartBtn,exitBtn;
JRadioButton r1,r2,r3,r4;
ButtonGroup bg;

String javaQuestions[];
String javaOptions[][];
int javaAnswers[];


String htmlQuestions[];
String htmlOptions[][];
int htmlAnswers[];


String cssQuestions[];
String cssOptions[][];
int cssAnswers[];

String que[];
String options[][];
int answers[];


int score=0;
int  queNo=0;







Q()
{

Font f=new Font("Arial",Font.BOLD,20);;


Questions();
options();
answers();
createFrame();

createComponent();
setBounds();
addComponent();
addListener();














l1.setText("Which your favourite language  select for test : ");
l1.setFont(f);


}



public static void main(String args[])
{

  new Q();

}


public void actionPerformed(ActionEvent e)
{
  

if(e.getSource()==javaBtn)
   {

   que=javaQuestions;
      options=javaOptions;
      answers=javaAnswers;

      hideComponent();
     showQuestions();

   }

 else if(e.getSource()==htmlBtn)
{
     que=htmlQuestions;
      options=htmlOptions;
      answers=htmlAnswers;
 
   
        hideComponent();
        showQuestions();

}


 else if (e.getSource()==cssBtn)
{
   que=cssQuestions;
   options=cssOptions;
   answers=cssAnswers;

      hideComponent();
      showQuestions();
   

}




else if(e.getSource()==nextBtn)
{

  if(bg.getSelection()==null)
  {

  JOptionPane.showMessageDialog(f,"PLZ select options ");
 
  }
  
  else{

  if(r1.isSelected()  && answers[queNo]==0) score++;
  else if(r2.isSelected()  && answers[queNo]==1) score++;
  else if(r3.isSelected()  && answers[queNo]==2) score++;
  else if(r4.isSelected()  && answers[queNo]==3) score++;
  queNo++; 
  
  

  }

 if(queNo< que.length)
  {
    bg.clearSelection();
   showQuestions();
    
  
  }


 else {
          l1.setText("Quiz Finished  ");
          
          r1.setVisible(false);
          
          r2.setVisible(false);
          r3.setVisible(false);
          r4.setVisible(false);
          nextBtn.setEnabled(false);
          
          homeBtn.setVisible(true);
          restartBtn.setVisible(true);
           exitBtn.setVisible(true);


         JOptionPane.showMessageDialog(f,"your score is "+score  );



     }


 


}

else if(e.getSource()==homeBtn)
  {
  
  
     showHomePage();



   }


else if(e.getSource()==restartBtn)
  {   

 nextBtn.setEnabled(true);
 bg.clearSelection();


  queNo=0;
  score=0;



  
  showQuestions();


   }



else if(e.getSource()==exitBtn)
  {
    
    System.exit(0);

   }


}


void createFrame()
{
  f=new JFrame(" mind Blowing  Quiz");
f.setLayout(null); 

 f.setSize(650,1050);
  f.setLocation(1280,0);



f.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
f.setVisible(true);
}



void createComponent()
{

l1=new  JLabel();
javaBtn=new JButton("JAVA");
htmlBtn=new JButton("HTML");
cssBtn=new JButton("CSS");
nextBtn=new JButton("NEXT");

r1=new JRadioButton();
r2=new JRadioButton();
r3=new JRadioButton();
r4=new JRadioButton();

bg=new ButtonGroup();


homeBtn=new JButton("HOME");
restartBtn=new JButton("RESTART");
exitBtn=new JButton("EXIT");



}

void setBounds()
{

l1.setBounds(40,50,700,80);
javaBtn.setBounds(220,220,300,70);
htmlBtn.setBounds(220,310,300,80);
cssBtn.setBounds(220,410,300,80);


homeBtn.setBounds(250,650,120,40);
restartBtn.setBounds(100,490,120,40);
exitBtn.setBounds(400,490,120,40);



r1.setBounds(40, 130, 450, 30);
r2.setBounds(40, 180, 450, 30);
r3.setBounds(40, 230, 450, 30);
r4.setBounds(40, 280, 450, 30);

nextBtn.setBounds(250, 350, 120, 40);



}

void  addComponent()
{

f.add(l1);
f.add(javaBtn);
f.add(htmlBtn);
f.add(cssBtn);

bg.add(r1);
bg.add(r2);
bg.add(r3);
bg.add(r4);

f.add(r1);
f.add(r2);
f.add(r3);
f.add(r4);

f.add(nextBtn);

f.add(homeBtn);
f.add(restartBtn);
f.add(exitBtn);


r1.setVisible(false);
    r2.setVisible(false);
    r3.setVisible(false);
    r4.setVisible(false);

homeBtn.setVisible(false);
restartBtn.setVisible(false);
exitBtn.setVisible(false);

}



void  hideComponent()
{

l1.setVisible(false);
javaBtn.setVisible(false);
htmlBtn.setVisible(false);
cssBtn.setVisible(false);




}


void addListener()
{

javaBtn.addActionListener(this);
htmlBtn.addActionListener(this);
cssBtn.addActionListener(this);
nextBtn.addActionListener(this);




homeBtn.addActionListener(this);
restartBtn.addActionListener(this);
exitBtn.addActionListener(this);

}



void showQuestions()
{

f.revalidate();
f.repaint();


homeBtn.setVisible(false);
restartBtn.setVisible(false);
exitBtn.setVisible(false);


l1.setVisible(true);
r1.setVisible(true);
r2.setVisible(true);
r3.setVisible(true);
r4.setVisible(true);
nextBtn.setVisible(true);

l1.setText(que[queNo]);
r1.setText(options[queNo][0]);
r2.setText(options[queNo][1]);
r3.setText(options[queNo][2]);
r4.setText(options[queNo][3]);




}

void Questions()
{

javaQuestions=new String[]
{
"Which keyword is used to inherit a class in Java?",
    "Which method is the entry point of a Java program?",
    "Which of the following is a valid data type in Java?"



};

htmlQuestions=new  String[]
{
     "What does HTML stand for?",
    "Which HTML tag is used to create a hyperlink?",
    "Which HTML tag is used to insert an image?"


};


cssQuestions=new  String[]
{

    "What does CSS stand for?",
    "Which property is used to change the text color in CSS?",
    "Which CSS property is used to change the background color?"


};






}

void options()
{

javaOptions=new String[][]
{

{"implements", "extends", "inherit", "super"},
    {"start()", "run()", "main()", "init()"},
    {"integer", "real", "float", "decimal"}



};


htmlOptions=new String[][]
{

{"Hyper Text Markup Language", "High Text Machine Language", "Hyper Transfer Markup Language", "Home Tool Markup Language"},
    {"<link>", "<a>", "<href>", "<url>"},
    {"<image>", "<img>", "<picture>", "<src>"}



};



cssOptions=new String[][]
{

{"Creative Style Sheets", "Cascading Style Sheets", "Computer Style Sheets", "Colorful Style Sheets"},
    {"font-color", "text-color", "color", "foreground"},
    {"bgcolor", "background-color", "background", "color"}



};



}

void answers()
{
  javaAnswers=new int[]{1, 2, 2};
  htmlAnswers=new int[]{0, 1, 1};
  cssAnswers=new int[]{1, 2, 1};

  




}




void  showHomePage()
{
    homeBtn.setVisible(false);
    restartBtn.setVisible(false);
    exitBtn.setVisible(false);
    nextBtn.setVisible(false);
    nextBtn.setEnabled(true);

    

    javaBtn.setVisible(true);
      htmlBtn.setVisible(true);
      cssBtn.setVisible(true);

     bg.clearSelection();
      
       

       queNo=0;
        score=0;




 
l1.setText("Which your favourite language  select for test : ");



}




}

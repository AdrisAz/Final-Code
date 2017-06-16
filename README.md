import java.awt.Color;
import java.awt.Container;
import java.awt.Font;
import java.awt.GridLayout;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import java.util.Random;

import javax.swing.ImageIcon;
import javax.swing.JButton;
import javax.swing.JFrame;
import javax.swing.JLabel;
import javax.swing.JPanel;
import javax.swing.JTextArea;

public class Game {	
	JFrame window;
	Container con;
	JPanel titleNamePanel, startButtonPanel, mainTextPanel, choiceButtonPanel, playerPanel, imagePanel, hpPanel, weaponPanel;
	JLabel titleNameLabel, hpLabel, hpLabelNumber, weaponLabel, weaponLabelName, imageLabel;
	Font titleFont = new Font("Times New Roman", Font.BOLD, 73);
	Font normalFont = new Font("Times New Roman", Font.BOLD, 25);
	Font choiceFont = new Font("Times New Roman", Font.BOLD, 22);
	JButton startButton, choice1, choice2, choice3, choice4;
	int playerHP, zombieHP;
	String weapon, position;
	ImageIcon image;
	JTextArea mainTextArea;
	
	TitleScreenHandler tsHandler = new TitleScreenHandler();
	ChoiceHandler choiceHandler = new ChoiceHandler();

	
	public static void main(String[] args) {
		// TODO Auto-generated method stub
			new Game();
	}
	
	public Game(){
		
		window = new JFrame();//Panel initialization 
		window.setSize(1280,720);//Size of window
		window.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);//Able to close program
		window.getContentPane().setBackground(Color.black);//Colour of window
		window.setLayout(null);//Disable default layout for game
		window.setVisible(true);//To see the window
		con = window.getContentPane();//Base layer
		
		titleNamePanel = new JPanel();//Panel initialization 
		titleNamePanel.setBounds(330, 100, 650, 150);//Size and location of panel
		titleNamePanel.setBackground(Color.black);//Colour of panel
		titleNameLabel = new JLabel("Zombie Apocalypse");//Text for title to be placed on panel
		titleNameLabel.setForeground(Color.white);//Colour of Text
		titleNameLabel.setFont(titleFont);//Apply font to text
		
		startButtonPanel = new JPanel();//Initialization of button frame
		startButtonPanel.setBounds(530, 400, 200, 100);//Size and location of button frame
		startButtonPanel.setBackground(Color.black);//Colour of button frame
		startButton = new JButton("Begin Game");//Button initialization 
		startButton.setBackground(Color.black);//Colour of button background
		startButton.setForeground(Color.white);//Colour of text on top of button
		startButton.setFont(normalFont);//Apply font to button text
		startButton.addActionListener(tsHandler);//Forwards to "TitleScreenHandler" ActionListener when button is clicked
		startButton.setFocusPainted(false);//Disable button focus
		//Alternate way to remove focus: "startButton.setFocusable(false);"
		
		titleNamePanel.add(titleNameLabel);//Place text on Panel
		startButtonPanel.add(startButton);//Place button on panel
		
		con.add(titleNamePanel);//Add panel to container, (Text panel Layer)
		con.add(startButtonPanel);//Add panel to container, (Button layer)
		window.setVisible(true);//To see the window
	}
	
	public void createGameScreen(){
		
		titleNamePanel.setVisible(false);//Disables this panel when createGameScreen is called
		startButtonPanel.setVisible(false);//Disables this panel when createGameScreen is called
		mainTextPanel = new JPanel();//Text panel initialization 
		mainTextPanel.setBounds(80, 100, 1150, 250);//Size and location of panel
		mainTextPanel.setBackground(Color.black);//Colour of panel
		mainTextPanel.setOpaque(false);//Set panel to transparent
		con.add(mainTextPanel);//Add panel to container, (Text panel Layer)
		
		mainTextArea = new JTextArea();//Initializes placement for text
		mainTextArea.setBounds(100, 100, 1150, 250);//Size and location of area
		mainTextArea.setOpaque(false);//Set panel to transparent
		mainTextArea.setForeground(Color.white);//Colour of text in area
		mainTextArea.setFont(normalFont);//Apply font to text
		mainTextArea.setLineWrap(true);//Apply a text wrap function
		mainTextArea.setWrapStyleWord(true);//Apply a specific (word) text wrap function
		mainTextPanel.add(mainTextArea);//Add text area to Text panel, (Text area layer)
		
		choiceButtonPanel = new JPanel();//Initialization of button frame
		choiceButtonPanel.setBounds(210, 350, 800, 250);//Size and location of panel
		choiceButtonPanel.setOpaque(false);//Set panel to transparent
		choiceButtonPanel.setLayout(new GridLayout(4,1));//Formats buttons to four individual rows
		con.add(choiceButtonPanel);//Add panel to container, (Button layer)
		
		choice1 = new JButton("Choice 1");//Button initialization
		choice1.setOpaque(false);//Set button to transparent
		choice1.setForeground(Color.black);//Colour of text on top of button
		choice1.setFont(normalFont);//Apply font to text on button
		choice1.setFocusPainted(false);//Disable button focus
		choice1.addActionListener(choiceHandler);//Forwards to "ChoiceHandler" ActionListener when button is clicked
		choice1.setActionCommand("c1");//Identifies to program which specific choice this button correlates to
		choiceButtonPanel.add(choice1);//Add Button on panel
		
		choice2 = new JButton("Choice 2");//Button initialization
		choice2.setOpaque(false);//Set button to transparent
		choice2.setForeground(Color.black);//Colour of text on top of button
		choice2.setFont(normalFont);//Apply font to text on button
		choice2.setFocusPainted(false);//Disable button focus
		choice2.addActionListener(choiceHandler);//Forwards to "ChoiceHandler" ActionListener when button is clicked
		choice2.setActionCommand("c2");//Identifies to program which specific choice this button correlates to
		choiceButtonPanel.add(choice2);//Add Button on panel
		
		choice3 = new JButton("Choice 3");//Button initialization
		choice3.setOpaque(false);//Set button to transparent
		choice3.setForeground(Color.black);//Colour of text on top of button
		choice3.setFont(normalFont);//Apply font to text on button
		choice3.setFocusPainted(false);//Disable button focus
		choice3.addActionListener(choiceHandler);//Forwards to "ChoiceHandler" ActionListener when button is clicked
		choice3.setActionCommand("c3");//Identifies to program which specific choice this button correlates to
		choiceButtonPanel.add(choice3);//Add Button on panel
		
		choice4 = new JButton("Choice 4");//Button initialization
		choice4.setOpaque(false);//Set button to transparent
		choice4.setForeground(Color.black);//Colour of text on top of button
		choice4.setFont(normalFont);//Apply font to text on button
		choice4.setFocusPainted(false);//Disable button focus
		choice4.addActionListener(choiceHandler);//Forwards to "ChoiceHandler" ActionListener when button is clicked
		choice4.setActionCommand("c4");//Identifies to program which specific choice this button correlates to
		choiceButtonPanel.add(choice4);//Add Button on panel
		
		hpPanel = new JPanel();
		hpPanel.setBounds(300, 20, 800, 50);//Size and location of panel
		hpPanel.setOpaque(false);//Set panel to transparent
		hpPanel.setBackground(Color.black);//Colour of panel
		hpPanel.setLayout(new GridLayout(1,4));//Layout of panel to four columns
		con.add(hpPanel);//Add panel to container
		
		weaponPanel = new JPanel();
		weaponPanel.setBounds(640, 20, 800, 50);//Size and location of panel
		weaponPanel.setOpaque(false);//Set panel to transparent
		weaponPanel.setBackground(Color.black);//Colour of panel
		weaponPanel.setLayout(new GridLayout(1,4));//Layout of panel to four columns
		con.add(weaponPanel);//Add panel to container
		
		playerPanel = new JPanel();//Panel initialization to hold player information
		playerPanel.setBounds(370, 20, 800, 50);//Size and location of panel
		playerPanel.setOpaque(false);//Set panel to transparent
		playerPanel.setBackground(Color.black);//Colour of panel
		playerPanel.setLayout(new GridLayout(1,4));//Layout of panel to four columns
		con.add(playerPanel);//Add panel to container
		
		hpLabel = new JLabel("HP:");//Text for HP label to be placed
		hpLabel.setFont(normalFont);//Font selection
		hpLabel.setForeground(Color.white);//Font colour
		hpPanel.add(hpLabel);//Add HP text to  panel
		
		hpLabelNumber = new JLabel();//Text for HP value to be placed
		hpLabelNumber.setFont(normalFont);//Font selection
		hpLabelNumber.setForeground(Color.white);//Font colour
		playerPanel.add(hpLabelNumber);//Add label to panel
		
		weaponLabel = new JLabel("Weapon:");//Text for weapon label to be placed
		weaponLabel.setFont(normalFont);//Font selection
		weaponLabel.setForeground(Color.white);//Font colour
		weaponPanel.add(weaponLabel);//Add label to panel
		
		weaponLabelName = new JLabel();//Text for weapon name to be placed
		weaponLabelName.setFont(normalFont);//Font selection
		weaponLabelName.setForeground(Color.white);//Font colour
		playerPanel.add(weaponLabelName);//Add label to panel
		
		imagePanel = new JPanel();
		imagePanel.setBounds(1, 1, 1280, 720);
		imagePanel.setBackground(Color.white);
		
		imageLabel = new JLabel();
		
		image = new ImageIcon(".//res//dforest.jpg");
		
		imageLabel.setIcon(image);
		imagePanel.add(imageLabel);
		
		con.add(imagePanel);
		
		playerSetup();//Directs program to playerSetup method
		
	}
	public void playerSetup(){//Initializes the playerSetup method
		playerHP = 100;//Set initial player's HP
		zombieHP = 100;//Set initial enemy's HP
		weapon = "Machete";//Set initial player's weapon
		weaponLabelName.setText(weapon);//Display weapon text on label
		hpLabelNumber.setText("" + playerHP);//Display integer HP value
		
		
		mainScreen();//Directs to main method
	}
			public void mainScreen()
	{
		playerPanel.validate();//Refreshes the panel
		playerPanel.repaint();//Tells program that panel needs refreshing
		choice2.setVisible(false);//Sets the buttons to invisible
		choice3.setVisible(false);//Sets the buttons to invisible
		choice4.setVisible(false);//Sets the buttons to invisible
		position = "mainScreen";//Indication of which method is currently running
		mainTextArea.setText("You are on a truck going to your best friend, Marty B’s,"
				+ "house  when you look out your driver's window to see something weird. "
				+ "You stop your truck to go out and see what it is and you notice that it is a humanoid figure in the woods."
				+ "You go to see if he is alright when you notice a foul smell and then see his literal dead stare looking right into your eyes, "
				+ "you see that he has a large piece of his shoulder bitten off with a disgusting amount of exposed skin. "
				+ "You ask him what happened but he only answers with a moan.You continue to stare back at the figure, then out of nowhere he attacks. ");//Placement for text
		choice1.setText("Continue");//Display text on button
		choice2.setText("");//Display text on button
		choice3.setText("");//Display text on button
		choice4.setText("");//Display text on button
	}
			public void mainScreencont()
	{
		playerPanel.validate();//Refreshes the panel
		playerPanel.repaint();//Tells program that panel needs refreshing
		choice2.setVisible(true);//Sets the buttons to invisible
		choice3.setVisible(true);//Sets the buttons to invisible
		choice4.setVisible(false);//Sets the buttons to invisible
		position = "mainScreencont";//Indication of which method is currently running
		mainTextArea.setText(" He starts running at you with that same dead stare locked onto you as his mouth is wide open."
				+ " You run as fast as you can back to your truck, lock the door and speed away with no hesitation."
				+ " When you are in the truck you keep asking yourself what that guy was doing,"
				+ " then you realize that even though you never thought the day would come,"
				+ " you realize that the world has gone into a ZOMBIE APOCALYPSE."
				+ " You keep driving to Marty B’s house that is just 10 minutes away and you see that the road is blocked by hundreds of humanoid figures"
				+ " similarly to the one that tried to eat you earlier."
				+ " You step on the brakes before getting any closer and…..You have to make a choice now, do you:");//Placement for text
		choice1.setText("Try to drive through the zombies");//Display text on button
		choice2.setText("Turn your truck around and try to find a different route");//Display text on button
		choice3.setText("Try to fight through the zombies");//Display text on button
		choice4.setText("");//Display text on button 
	}
			public void drivetru()
		{
			playerPanel.validate();//Refreshes the panel
			playerPanel.repaint();//Tells program that panel needs refreshing
			choice2.setVisible(true);//Sets the buttons to invisible
			choice3.setVisible(true);//Sets the buttons to invisible
			choice4.setVisible(false);//Sets the buttons to invisible
			position = "drivetru";//Indication of which method is currently running
			mainTextArea.setText("You stomp on the gas pedal as hard as you can and try to bust through the zombies."
					+ " You manage to get out the other end but they end up ripping out the exhaust pipe and part of the  hood."
					+ " Do you:");//Placement for text
			choice1.setText("Keep on driving for as long as you can ");//Display text on button
			choice2.setText("Hold up in your truck hoping someone comes that can rescue you ");//Display text on button
			choice3.setText("Try and find parts for your truck");//Display text on button
			 
		}
			public void drivecont()
			{
				playerPanel.validate();//Refreshes the panel
				playerPanel.repaint();//Tells program that panel needs refreshing
				choice2.setVisible(false);//Sets the buttons to invisible
				choice3.setVisible(false);//Sets the buttons to invisible
				choice4.setVisible(false);//Sets the buttons to invisible
				position = "drivecont";//Indication of which method is currently running
				choice1.setText("Continue");//Display text on button
				choice2.setText("");//Display text on button
				choice3.setText("");//Display text on button
				choice4.setText("");//Display text on button 
				mainTextArea.setText("You keep driving for as long as you can towards Marty's house."
						+ " As you are driving you notice that your gas tank is also leaking so you stomp on the gas so you can use as much gas as you can well it is in your tank."
						+ " As you hit the gas the dangling exhaust pipe starts to spark and catches the dripping gas on fire."
						+ " The flames are starting to cover the car and before you can do anything the car blows up. YOU DIE");
			}
			public void holdup()
			{
				playerPanel.validate();//Refreshes the panel
				playerPanel.repaint();
				choice1.setText("Continue");//Tells program that panel needs refreshing
				choice2.setVisible(false);//Sets the buttons to invisible
				choice3.setVisible(false);//Sets the buttons to invisible
				choice4.setVisible(false);//Sets the buttons to invisible
				position = "holdup";//Indication of which method is currently running
				mainTextArea.setText("You decide to lock your doors and you figure out that you have enough food and water for only 2 days."
						+ " 2 days pass and you stay in one spot but the only thing that is coming towards you is zombies and not help. "
						+ " As you hit the gas the dangling exhaust pipe starts to spark and catches the dripping gas on fire."
						+ " You have ran out of food and water but at this point you are completely surrounded by zombies and you realize you no matter what you do you won't make it out. YOU DIE");
						
			}
			public void walk()
			{
				playerPanel.validate();//Refreshes the panel
				playerPanel.repaint();//Tells program that panel needs refreshing
				choice2.setVisible(true);//Sets the buttons to invisible
				choice3.setVisible(false);//Sets the buttons to invisible
				choice4.setVisible(false);//Sets the buttons to invisible
				position = "walk";//Indication of which method is currently running
				mainTextArea.setText("You leave your truck and follow the road away from the zombies."
						+ " You walk for an hour before you can see the town your friend lives in."
						+ " As you look at the town you can’t see anyone anywhere in the town. Do you:");//Placement for text
				choice1.setText("Keep walking and pass the town you friend lives in");//Display text on button
				choice2.setText("Walk into the town and look for your friend");//Display text on button
				choice3.setText("");//Display text on button
				
				choice4.setText("");//Display text on button 
			}
			public void walkcont()
				{
					playerPanel.validate();//Refreshes the panel
					playerPanel.repaint();//Tells program that panel needs refreshing
					choice2.setVisible(true);//Sets the buttons to invisible
					choice3.setVisible(false);//Sets the buttons to invisible
					choice4.setVisible(false);//Sets the buttons to invisible
					position = "walkcont";//Indication of which method is currently running
					mainTextArea.setText("You walk past the town to search for your friend Marty B."
							+ " As you are walking you notice that there is a zombie on the road in front out you."
							+ " As you get closer to the zombie you notice that it is your best friend Marty B."
							+ " He notices you and starts to come towards you and you have to make a choice. Do you:");//Placement for text
					choice1.setText("Kill your friend because he has turned into a zombie.");//Display text on button
					choice2.setText("Run away from him ");//Display text on button
					choice3.setText("");//Display text on button
					
					choice4.setText("");//Display text on button 
					
				}
			public void killYourFriend()
				{
					playerPanel.validate();//Refreshes the panel
					playerPanel.repaint();//Tells program that panel needs refreshing
					choice2.setVisible(true);//Sets the buttons to invisible
					choice3.setVisible(false);//Sets the buttons to invisible
					choice4.setVisible(false);//Sets the buttons to invisible
					position = "killYourFriend";//Indication of which method is currently running
					mainTextArea.setText("As you are approaching Marty you pull out your (Insert Weapon) And go to hit him. With one fast strike to the head you kill him making him fall to the ground. "
							+ "As he is falling you see a note and a key fall out of his pocket. The note tells you to go to the next town over and kill the zombie that killed Marty B and that the zombie will have a piece of Marty's shirt around his neck. "
							+ "You leave your friend on the ground and walk away. You keep walking down the road till you reach a town. You are very hungry and tired from walking all day. "
							+ "You go into the town and look down the streets to see a pack of 5 zombies.  Do you:");//Placement for text
					choice1.setText("Go and fight the zombies");//Display text on button
					choice2.setText("Just keep looking for the zombie that killed Marty B");//Display text on button
					choice3.setText("");//Display text on button
					
					choice4.setText("");//Display text on button 
				}
			public void lookForZombie()
				{
					playerPanel.validate();//Refreshes the panel
					playerPanel.repaint();//Tells program that panel needs refreshing
					choice2.setVisible(true);//Sets the buttons to invisible
					choice3.setVisible(false);//Sets the buttons to invisible
					choice4.setVisible(false);//Sets the buttons to invisible
					position = "lookForZombie";//Indication of which method is currently running
					mainTextArea.setText("You leave the zombies and look around for the one that killed your friend. You start walking the town and you realize that the town is mostly empty except for just a few zombies. "
							+ "Every  zombie you see you look at its neck but don't see Marty's shirt. Just before you are about to give up you hear a roar from inside one of the houses. "
							+ "You look around and see 2 boxes that are locked one contains a weapon and one contains extra health. Do you:");//Display text on button
					choice1.setText("Pick the weapon");//Display text on button
					choice2.setText("Pick the health ");//Display text on button
					choice3.setText("");//Display text on button
					choice4.setText("");//Display text on button 
				}
			public void pickWeapon()
				{
					playerPanel.validate();//Refreshes the panel
					playerPanel.repaint();//Tells program that panel needs refreshing
					choice2.setVisible(false);//Sets the buttons to invisible
					choice3.setVisible(false);//Sets the buttons to invisible
					choice4.setVisible(false);//Sets the buttons to invisible
					position = "pickWeapon";//Indication of which method is currently running
					mainTextArea.setText("You grab your weapon and go into fight the zombie that killed your friend. "
							+ "You see the zombie in the living room but you notice that it is not just any zombie it is a ZOMBIE BEAR. "
							+ "You go to attack it");//Display text on button
					choice1.setText("ATTACK!!");//Display text on button
					choice2.setText("");//Display text on button
					choice3.setText("");//Display text on button
					choice4.setText("");//Display text on button 
					}
			public void pickHealth()
				{
					playerPanel.validate();//Refreshes the panel
					playerPanel.repaint();//Tells program that panel needs refreshing
					choice2.setVisible(false);//Sets the buttons to invisible
					choice3.setVisible(false);//Sets the buttons to invisible
					choice4.setVisible(false);//Sets the buttons to invisible
					position = "pickHealth";//Indication of which method is currently running
					mainTextArea.setText("You grab your health and go into fight the zombie that killed your friend."
							+ " You see the zombie in the living room but you notice that it is not just any zombie it is a ZOMBIE BEAR. "
							+ "You go to attack it ");//Display text on button
					choice1.setText("ATTACK!!");//Display text on button
					choice2.setText("");//Display text on button
					choice3.setText("");//Display text on button
					choice4.setText("");//Display text on button 
					}
			public void victory()
				{
					playerPanel.validate();//Refreshes the panel
					playerPanel.repaint();//Tells program that panel needs refreshing
					choice1.setVisible(false);
					choice2.setVisible(false);//Sets the buttons to invisible
					choice3.setVisible(false);//Sets the buttons to invisible
					choice4.setVisible(false);//Sets the buttons to invisible
					position = "victory";//Indication of which method is currently running
					mainTextArea.setText("You avenge your friend and the bear releases a mysterious gas into the atmosphere. "
							+ "As the gas reaches the zombies it suddenly destroys whatever the zombies have left of a brain, and kills all of them leaving the living alone. "
							+ "You realize that you didn't just avenge your friend, but you also saved the whole world!!");//Display text on button
					choice1.setText("ATTACK!!");//Display text on button
					choice2.setText("");//Display text on button
					choice3.setText("");//Display text on button
					choice4.setText("");//Display text on button 
					}
			public void playerAttack(){//Initializes the player attack screen method
					playerPanel.validate();//Refreshes the panel
					playerPanel.repaint();//Tells program that panel needs refreshing
					position = "playerAttack";//Indication of which method is currently running
					
					Random rand=new Random();
					
					int playerDamage = 0;//Set variable for damage player does
					
					if(weapon.equals("Machete")){//Indicating that if the Machete is equipped then continue below
						playerDamage = new java.util.Random().nextInt(50);//Allows to randomly pick the damage value that player does (0-49)
					}
					else if (weapon.equals("Magic Sword")){//Indicating that if the Magic Sword is equipped then continue below
						playerDamage = rand.nextInt(40) + 5;//Allows to randomly pick the damage value that player does (0-79)
					}
					
					mainTextArea.setText("You attacked the zombie and dealt " + playerDamage + " damage");//Placement for text
					
					zombieHP = zombieHP - playerDamage;//Calculation for enemy's health
					
					choice1.setText("Continue");//Display text on button
					choice2.setText("");//Display text on button
					choice3.setText("");//Display text on button
					choice4.setText("");//Display text on button
				}
			public void zombieAttack(){//Initializes the zombie attack screen method
					playerPanel.validate();//Refreshes the panel
					playerPanel.repaint();//Tells program that panel needs refreshing
					position = "zombieAttack";//Indication of which method is currently running
					
					int zombieDamage = 0;//Set variable for damage zombie does
					
					zombieDamage = new java.util.Random().nextInt(30);//Allows to randomly pick the damage value that zombie does (0-29)
					
					mainTextArea.setText("The zombie attacked and dealt " + zombieDamage + " damage");//Placement for text
				
					playerHP = playerHP - zombieDamage;//Calculation for player's health
					hpLabelNumber.setText(""+playerHP);//Display updated HP value
					
					choice1.setText("Attack");//Display text on button
					choice2.setText("");//Display text on button
					choice3.setText("");//Display text on button
					choice4.setText("");//Display text on button
				}
			public void win(){//Initializes the win screen method
					playerPanel.validate();//Refreshes the panel
					playerPanel.repaint();//Tells program that panel needs refreshing
					position = "win";//Indication of which method is currently running
					
					mainTextArea.setText("You have killed the zombie.");//Placement for text
				
					choice1.setText("Continue");//Display text on button
					choice2.setText("");//Display text on button
					choice3.setText("");//Display text on button
					choice4.setText("");//Display text on button
				}
			public void lose(){//Initializes the lose screen method
					playerPanel.validate();//Refreshes the panel
					playerPanel.repaint();//Tells program that panel needs refreshing
					position = "lose";//Indication of which method is currently running
					
					mainTextArea.setText("You are dead.\n\nGAME OVER");//Placement for text
					
					choice1.setText("");//Display text on button
					choice2.setText("");//Display text on button
					choice3.setText("");//Display text on button
					choice4.setText("");//Display text on button
					choice1.setVisible(false);//Sets the buttons to invisible
					choice2.setVisible(false);//Sets the buttons to invisible
					choice3.setVisible(false);//Sets the buttons to invisible
					choice4.setVisible(false);//Sets the buttons to invisible
				}
			public void runAwayMarty()
				{
					playerPanel.validate();//Refreshes the panel
					playerPanel.repaint();//Tells program that panel needs refreshing
					choice2.setVisible(false);//Sets the buttons to invisible
					choice3.setVisible(false);//Sets the buttons to invisible
					choice4.setVisible(false);//Sets the buttons to invisible
					position = "runAwayMarty";//Indication of which method is currently running
					mainTextArea.setText("You start running away from Marty B. as you are running you trip so you look back at him to see if he is chasing you."
							+ " You see that he is but as you are looking back another zombie walks onto the rad and blocks your path. "
							+ "You run into the zombie knocking both of you to the floor you try to get up but the zombie grabs onto you. "
							+ "Before you can do anything both marty b and the other zombie have already bitten you. YOU DIE");//Placement for text
					choice1.setText("Continue");//Display text on button
					choice2.setText("");//Display text on button
					choice3.setText("");//Display text on button
	                choice4.setText("");//Display text on button 
				}
			public void fightZombie1()
				{
					playerPanel.validate();//Refreshes the panel
					playerPanel.repaint();//Tells program that panel needs refreshing
					choice2.setVisible(false);//Sets the buttons to invisible
					choice3.setVisible(false);//Sets the buttons to invisible
					choice4.setVisible(false);//Sets the buttons to invisible
					position = "fightZombie1";//Indication of which method is currently running
					mainTextArea.setText("You start running at the five zombies and hit the first one with your (insert weapon) in the head. You pull your (insert weapon) out and swing at the next zombie."
							+ " You keep swinging your weapon around and end up hitting one of the zombies. You try to pull your sword out but it's stuck. "
							+ "The other zombies are coming at you and you keep pulling at your (insert weapon) but it won't come out. You leave your (insert weapon) and try to run away."
							+ " As you are running you trip over a dead zombie and before you can even get up the three remaining zombies are on top of you. YOU DIE");//Display text on button
					choice1.setText("Continue");//Display text on button
					choice2.setText("");//Display text on button
					choice3.setText("");//Display text on button
					choice4.setText("");//Display text on button 
				}
			public void attack()
					{
						playerPanel.validate();//Refreshes the panel
						playerPanel.repaint();//Tells program that panel needs refreshing
						choice2.setVisible(true);//Sets the buttons to invisible
						choice3.setVisible(true);//Sets the buttons to invisible
						choice4.setVisible(true);//Sets the buttons to invisible
						position = "attack";//Indication of which method is currently running
						mainTextArea.setText("As you are approaching Marty you pull out your (Insert Weapon) And go to hit him"
								+ " With one fast strike to the head you kill him making him fall to the ground."
								+ " As he is falling you see a note and a key fall out of his pocket."
								+ " The note tells you to go to the next town over and kill the zombie that killed Marty B and that the zombie will have a piece of Marty's shirt around his neck."
								+ " You leave your friend on the ground and walk away. "
								+ " You leave your friend on the ground and walk away. "
								+ " You are very hungry and tired from walking all day you do into the town and look down the streets to see a pack of 5 zombies Do you:");//Placement for text
						choice1.setText("Go and fight the zombies");//Display text on button
						choice2.setText("Just keep looking for the zombie that killed Marty B.");//Display text on button
						choice3.setText("");//Display text on button
						
						choice4.setText("");//Display text on button 
					}
			public void fight()
						{
							playerPanel.validate();//Refreshes the panel
							playerPanel.repaint();//Tells program that panel needs refreshing
							choice2.setVisible(true);//Sets the buttons to invisible
							choice3.setVisible(true);//Sets the buttons to invisible
							choice4.setVisible(true);//Sets the buttons to invisible
							position = "fight";//Indication of which method is currently running
							mainTextArea.setText("You start running a the five zombies and hit the first one with your (insert weapon) in the head."
									+ " ou pull your (insert weapon) out and swing at the next zombie."
									+ " You keep swinging your weapon around and end up hitting one of the zombies."
									+ " You try to pull your sword out but it's stuck. "
									+ " The other zombies are coming at you and you keep pulling at your (insert weapon) but it won't come out. "
									+ " You leave your (insert weapon) and try to run away. "
									+ " As you are running you trip over a dead zombie and before you can even get up the three remaining zombies are on top of you. YOU DIE");//Placement for text
						}
			public void find()
						{
							playerPanel.validate();//Refreshes the panel
							playerPanel.repaint();//Tells program that panel needs refreshing
							choice2.setVisible(true);//Sets the buttons to invisible
							choice3.setVisible(true);//Sets the buttons to invisible
							choice4.setVisible(true);//Sets the buttons to invisible
							position = "find";//Indication of which method is currently running
							mainTextArea.setText("You leave the zombies and look around for the one that killed your friend. "
									+ " You start walking the town and you realize that the town is mostly empty except for just a few zombies."
									+ " Every  zombie you see you look at its neck but don't see Marty's shirt."
									+ " Just before you are about to give up you hear a roar from inside one of the houses."
									+ " You look around and see 2 boxes that are locked one contains a weapon and one contains extra health. Do you:");//Placement for text
							choice1.setText("Pick the weapon");//Display text on button
							choice2.setText("Pick the health ");//Display text on button
							choice3.setText("");//Display text on button
							
							choice4.setText("");//Display text on button 
						}
			public void weapon()
							{
								playerPanel.validate();//Refreshes the panel
								playerPanel.repaint();//Tells program that panel needs refreshing
								choice2.setVisible(true);//Sets the buttons to invisible
								choice3.setVisible(true);//Sets the buttons to invisible
								choice4.setVisible(true);//Sets the buttons to invisible
								position = "weapon";//Indication of which method is currently running
								mainTextArea.setText("You grab your weapon and go into fight the zombie that killed your friend. "
										+ " You see the zombie in the living room but you notice that it is not just any zombie it is a ZOMBIE BEAR. "
										+ " You go to attack it  (FIGHT) (if you win) you avenge your friend and release a gas into the atmosphere from in the bear. "
										+ " As the gas reaches zombies it destroys the brain and kills all the zombies but leaves the living alone. "
										+ " You realize that you didn't just avenge your friend but you also saved the whole world");//Placement for text
								dead();
							}
			public void health()
							{
								playerPanel.validate();//Refreshes the panel
								playerPanel.repaint();//Tells program that panel needs refreshing
								choice2.setVisible(true);//Sets the buttons to invisible
								choice3.setVisible(true);//Sets the buttons to invisible
								choice4.setVisible(true);//Sets the buttons to invisible
								position = "health";//Indication of which method is currently running
								mainTextArea.setText("You grab your health and go into fight the zombie that killed your friend. "
										+ " You see the zombie in the living room but you notice that it is not just any zombie it is a ZOMBIE BEAR. "
										+ " You go to attack it  (FIGHT) (if you win) you avenge your friend and release a gas into the atmosphere from in the bear. "
										+ " As the gas reaches zombies it destroys the brain and kills all the zombies but leaves the living alone. "
										+ " You realize that you didn't just avenge your friend but you also saved the whole world");//Placement for text
							}
			public void leave()
					{
						playerPanel.validate();//Refreshes the panel
						playerPanel.repaint();//Tells program that panel needs refreshing
						choice2.setVisible(true);//Sets the buttons to invisible
						choice3.setVisible(true);//Sets the buttons to invisible
						choice4.setVisible(true);//Sets the buttons to invisible
						position = "leave";//Indication of which method is currently running
						mainTextArea.setText(""
								+ ""
								+ ""
								+ ""
								+ ""
								+ "");//Placement for text
						choice1.setText("");//Display text on button
						choice2.setText("");//Display text on button
						choice3.setText("");//Display text on button
						
						choice4.setText("");//Display text on button 
					}
			public void findfriend()
				{
					playerPanel.validate();//Refreshes the panel
					playerPanel.repaint();//Tells program that panel needs refreshing
					choice2.setVisible(true);//Sets the buttons to invisible
					choice3.setVisible(false);//Sets the buttons to invisible
					choice4.setVisible(false);//Sets the buttons to invisible
					position = "findfriend";//Indication of which method is currently running
					mainTextArea.setText("You walk into the town looking down each street seeing if you can see anyone in the town."
							+ "The town seems completely empty with not a sign of life anywhere."
							+ "You walk to your friends house to see the door and windows boarded up."
							+ "Inside you see your best friend has been bit by a zombie and he is coming at you."
							+ "You panic and don’t know what to do. Do you:");//Placement for text
					choice1.setText("Pick up the chair beside you and hit him with it.");//Display text on button
					choice2.setText("Freeze up. Stand still and hope he does not see you.");//Display text on button
					choice3.setText("");//Display text on button
					
					choice4.setText("");//Display text on button 
				}
			public void pickUpChair()
				{
					playerPanel.validate();//Refreshes the panel
					playerPanel.repaint();//Tells program that panel needs refreshing
					choice2.setVisible(false);//Sets the buttons to invisible
					choice3.setVisible(false);//Sets the buttons to invisible
					choice4.setVisible(false);//Sets the buttons to invisible
					position = "pickUpChair";//Indication of which method is currently running
					mainTextArea.setText(" Your attack was ineffective, the zombie comes and attacks you, YOU DIE");//Placement for text
					choice1.setText("Continue");//Display text on button
					choice2.setText("");//Display text on button
					choice3.setText("");//Display text on button
					choice4.setText("");//Display text on button 
				}
			public void freezeUp()
				{
					playerPanel.validate();//Refreshes the panel
					playerPanel.repaint();//Tells program that panel needs refreshing
					choice2.setVisible(false);//Sets the buttons to invisible
					choice3.setVisible(false);//Sets the buttons to invisible
					choice4.setVisible(false);//Sets the buttons to invisible
					position = "freezeUp";//Indication of which method is currently running
					mainTextArea.setText(" Freeze up. Stand still and hope he does not see you. "
							+ "You stand still hoping that he will go around you but all he sees you as is food and he comes up to you and bites you turning you into a zombie. YOU DIE");//Placement for text
					choice1.setText("Continue");//Display text on button
					choice2.setText("");//Display text on button
					choice3.setText("");//Display text on button
					choice4.setText("");//Display text on button 
				}
			public void chairfight()
					{
						playerPanel.validate();//Refreshes the panel
						playerPanel.repaint();//Tells program that panel needs refreshing
						choice2.setVisible(true);//Sets the buttons to invisible
						choice3.setVisible(true);//Sets the buttons to invisible
						choice4.setVisible(true);//Sets the buttons to invisible
						position = "chairfight";//Indication of which method is currently running
						mainTextArea.setText("You grab the chair and hit him as hard as you can, knocking him to the ground."
								+ "You notice that even though he is on the ground he is still trying to come at you and you have no choice but to kill your best friend."
								+"You hit him with the chair again killing him but as you do you notice something on the ground."
								+"You bend down to pick it up and you see that it is a note from Marty and a key."
								+"In the note is says “Please go avenge my death and kill the zombie that killed me. He is in the next town over and will have my shirt wrapped around him.” Do you");//Placement for text
						choice1.setText("Make it your mission to kill the zombie that killed your best friend ");//Display text on button
						choice2.setText("Decide that marty is not worth it and just try to stay alive");//Display text on button
						choice3.setText("");//Display text on button
						
						choice4.setText("");//Display text on button 
					}
			public void mission()
						{
							playerPanel.validate();//Refreshes the panel
							playerPanel.repaint();//Tells program that panel needs refreshing
							choice2.setVisible(true);//Sets the buttons to invisible
							choice3.setVisible(true);//Sets the buttons to invisible
							choice4.setVisible(true);//Sets the buttons to invisible
							position = "mission";//Indication of which method is currently running
							mainTextArea.setText("You decide to go and find the zombie that killed your friend but before you go you want to find a weapon you look around and see a sword on the ground. "
									+ "You pick it up and start your quest."
									+"You leave the town and go to find the zombie that killed your friend."
									+"You start walking to the next town over to find the zombie. You keep walking till you reach the town."
									+"You go into the town and look down the streets to see a pack of 5 zombies.  Do you:");//Placement for text
							choice1.setText("Go and fight the zombies");//Display text on button
							choice2.setText("Just keep looking for the zombie that killed Marty B.");//Display text on button
							choice3.setText("");//Display text on button
							
							choice4.setText("");//Display text on button 
						}
			public void stayalive()
						{
							playerPanel.validate();//Refreshes the panel
							playerPanel.repaint();//Tells program that panel needs refreshing
							choice2.setVisible(true);//Sets the buttons to invisible
							choice3.setVisible(true);//Sets the buttons to invisible
							choice4.setVisible(true);//Sets the buttons to invisible
							position = "stayalive";//Indication of which method is currently running
							mainTextArea.setText("You decide to stay at the house and just try to stay alive.  "
									+ "In the house is food and water to stay alive for a year."
									+"You board up all the windows and doors and decide to stay in the house."
									+"As you are walking around the house looking for supplies a zombie jumps out at you when you open the bedroom door the zombie bites your throt and kills you. YOU DIE");//Placement for text
						}
			public void standstill()
					{
						playerPanel.validate();//Refreshes the panel
						playerPanel.repaint();//Tells program that panel needs refreshing
						choice2.setVisible(true);//Sets the buttons to invisible
						choice3.setVisible(true);//Sets the buttons to invisible
						choice4.setVisible(true);//Sets the buttons to invisible
						position = "standstill";//Indication of which method is currently running
						mainTextArea.setText("You stand still hoping that he will go around you but all he sees you as is food and he comes up to you and bites you turning you into a zombie. YOU DIE");//Placement for text
					}
			public void parts()
				{
					playerPanel.validate();//Refreshes the panel
					playerPanel.repaint();//Tells program that panel needs refreshing
					choice2.setVisible(true);//Sets the buttons to invisible
					choice3.setVisible(false);//Sets the buttons to invisible
					choice4.setVisible(false);//Sets the buttons to invisible
					position = "parts";//Indication of which method is currently running
					mainTextArea.setText("You get out and look around for parts for your car. "
							+"As you are looking for parts for your car the herd that you just drove through is walking towards you."
							+"You are opening up hoods of cars looking for the parts you need when you see the herd coming you panic and don’t know what to do. Do you:");//Placement for text
					choice1.setText("Run as fast as you can away from the zombies");//Display text on button
					choice2.setText("Get in a car, hide and hope they just pass by");//Display text on button
					choice3.setText("");//Display text on button
					choice4.setText("");//Display text on button
				}
			public void runFromZombies()
				{
					playerPanel.validate();//Refreshes the panel
					playerPanel.repaint();//Tells program that panel needs refreshing
					choice2.setVisible(false);//Sets the buttons to invisible
					choice3.setVisible(false);//Sets the buttons to invisible
					choice4.setVisible(false);//Sets the buttons to invisible
					position = "runFromZombies";//Indication of which method is currently running
					mainTextArea.setText("You start running towards Marty’s town. You start running away from the zombies and towards Marty's town. "
							+ "When you get to Marty's town you are completely out of breath but you did get away from the herd you walk through the town and notice that is is completely empty. "
							+ "You walk to Marty’s house and go inside. It looks compleatly empty but you keep looking for your friend. You go up into his room and open the door but as you do that 20 zombies start running out of his room and attack you. "
							+ "You try and run away but it is too late. YOU DIE");//Placement for text
					choice1.setText("Continue");//Display text on button
					choice2.setText("");//Display text on button
					choice3.setText("");//Display text on button
					choice4.setText("");//Display text on button
				}
			public void getInCarAndHide()
				{
					playerPanel.validate();//Refreshes the panel
					playerPanel.repaint();//Tells program that panel needs refreshing
					choice2.setVisible(true);//Sets the buttons to invisible
					choice3.setVisible(false);//Sets the buttons to invisible
					choice4.setVisible(false);//Sets the buttons to invisible
					position = "getInCarAndHide";//Indication of which method is currently running
					mainTextArea.setText("Get in a car, hide and hope they just pass by. You get in your truck hoping that the herd will just pass by. "
							+ "As you are waiting you notice that the zombies are getting closer but are stopping and surrounding your truck. "
							+ "You look out to see why they are stopping but one of the zombies sees you and starts rocking the truck more zombies come around and you realize that there is no way out. "
							+ "You open the door to make a run for it but as you do you are bite bye many zombies. YOU DIE");//Placement for text
					choice1.setText("Continue");//Display text on button
					choice2.setText("");//Display text on button
					choice3.setText("");//Display text on button
					choice4.setText("");//Display text on button
				}			
			public void turnaround()
			{
			playerPanel.validate();//Refreshes the panel
			playerPanel.repaint();//Tells program that panel needs refreshing
			choice2.setVisible(true);//Sets the buttons to invisible
			choice3.setVisible(false);//Sets the buttons to invisible
			choice4.setVisible(false);//Sets the buttons to invisible
			position = "turnaround";//Indication of which method is currently running
			mainTextArea.setText("You turn your truck around but as you do the zombies notice the movement and sound of your truck."
					+"You look in your rear view mirror and you start to see the herd of zombies coming towards you."
					+"You hit the gas as hard as you can and drive away from the zombies."
					+"As you are driving you turn onto a road that should lead you to Marty’s house."
					+"While you are driving you start to see zombies coming out of the trees."
					+"You look up ahead and see some zombies on the rad and more are walking towards it."
					+"You notice that soon the road will be completely covered by zombies.\nDo you:");//Placement for text
			choice1.setText("Speed up and try to get out before you get trapped");//Display text on button
			choice2.setText("Turn around and try to get out of the herd");//Display text on button
			choice3.setText("");//Display text on button
			choice4.setText("");//Display text on button
			}
			public void getOutHerd()
			{
			playerPanel.validate();//Refreshes the panel
			playerPanel.repaint();//Tells program that panel needs refreshing
			choice2.setVisible(true);//Sets the buttons to invisible
			choice3.setVisible(false);//Sets the buttons to invisible
			choice4.setVisible(false);//Sets the buttons to invisible
			position = "getOutHerd";//Indication of which method is currently running
			mainTextArea.setText("You turn your truck around and try to get out of the herd. "
					+ "As you turn it around you see that there are more zombies behind you. "
					+ "You start to drive out the way you came. As you are driving you get on another road and drive away from the zombies. "
					+ "You keep driving till you run out of gas. You decide that you are in a good enough spot and decide to sleep in your truck. "
					+ "The next morning you wake up and you realize that you are completely lost. "
					+ "You get out of your car and start walking. You keep walking until you can see a town. "
					+ "You start walking towards the town but you notice that there is a zombie in your path. Do you:");//Placement for text
			choice1.setText("Run past, around it");//Display text on button
			choice2.setText("Attack it");//Display text on button
			choice3.setText("");//Display text on button
			choice4.setText("");//Display text on button
			}
			public void attackZombie()
			{
			playerPanel.validate();//Refreshes the panel
			playerPanel.repaint();//Tells program that panel needs refreshing
			choice2.setVisible(true);//Sets the buttons to invisible
			choice3.setVisible(false);//Sets the buttons to invisible
			choice4.setVisible(false);//Sets the buttons to invisible
			position = "attackZombie";//Indication of which method is currently running
			mainTextArea.setText("You go to attack it the zombie and notice it is your friend Marty B. "
					+ "You throw him to the ground and he hits his head off of a rock. "
					+ "You look at him and you see something in his pocket. You reach in and pull out a note and a key. "
					+ "The note asks you to avenge his death and kill the zombie that infected him. "
					+ "It says that the zombie is in the town and that he will have his shirt wrapped around his neck. "
					+ "You decide that you are going to avenge your friend and walk to the town.  "
					+ "You go into the town and look down the streets to see a pack of 5 zombies. Do you:");//Placement for text
			choice1.setText("Go and fight the zombies");//Display text on button
			choice2.setText("Just keep looking for the zombie that killed Marty B");//Display text on button
			choice3.setText("");//Display text on button
			choice4.setText("");//Display text on button
			}
			public void getOutHerdCont()
			{
			playerPanel.validate();//Refreshes the panel
			playerPanel.repaint();//Tells program that panel needs refreshing
			choice2.setVisible(false);//Sets the buttons to invisible
			choice3.setVisible(false);//Sets the buttons to invisible
			choice4.setVisible(false);//Sets the buttons to invisible
			position = "getOutHerdCont";//Indication of which method is currently running
			mainTextArea.setText("You notice as you run past it that it is your friend Marty. "
					+ "You look at him as you are running but you don't slow down. You go into the town and see a group of zombies. "
					+ "You try to go into a house but they notice you are start following you. You go into one of the houses and try to hide in one of the rooms."
					+ "You open one door and three zombies come out. You try to turn around but there are zombies behind you too."
					+ "You try to run through them but one end up biting you turning you into a zombie. YOU DIE");//Placement for text
			choice1.setText("Continue");//Display text on button
			choice2.setText("");//Display text on button
			choice3.setText("");//Display text on button
			choice4.setText("");//Display text on button
			}
			public void speed()
			{
				playerPanel.validate();//Refreshes the panel
				playerPanel.repaint();//Tells program that panel needs refreshing
				choice2.setVisible(true);//Sets the buttons to invisible
				choice3.setVisible(true);//Sets the buttons to invisible
				choice4.setVisible(false);//Sets the buttons to invisible
				position = "speed";//Indication of which method is currently running
				mainTextArea.setText("You stomp on the gas as hard as you can hitting zombies as you try to get out. "
						+"As you are driving through the zombies you run over a spike and pop one of your tires."
						+"You try and keep driving but as you hit zombies your car gets slower and slower and you think you might not make it out. Do you:");//Placement for text
				choice1.setText("Keep trying to drive through by pushing on the gas");//Display text on button
				choice2.setText("Get out now and try and run to the forest");//Display text on button
				choice3.setText("Realize that there is no hope and just let the zombies take over");//Display text on button
				choice4.setText("");//Display text on button
			}
			public void drivetrucont()
				{
					playerPanel.validate();//Refreshes the panel
					playerPanel.repaint();//Tells program that panel needs refreshing
					choice2.setVisible(true);//Sets the buttons to invisible
					choice3.setVisible(false);//Sets the buttons to invisible
					choice4.setVisible(false);//Sets the buttons to invisible
					position = "drivetrucont";//Indication of which method is currently running
					mainTextArea.setText("You push on the gas as hard as you can to try and make it through the zombies. "
							+ "Well you are going you go over a nail and pop your other front tire. "
							+ "You try to keep going but end up getting stopped by the herd of zombies. "
							+ "You get completely surrounded by the zombies and there is no way out and you are left with only one choice. Do you:");//Placement for text
					choice1.setText("End it Yourself");//Display text on button
					choice2.setText("Get out and try to run");//Display text on button
				}
			public void endIt()
				{
					playerPanel.validate();//Refreshes the panel
					playerPanel.repaint();//Tells program that panel needs refreshing
					choice2.setVisible(false);//Sets the buttons to invisible
					choice3.setVisible(false);//Sets the buttons to invisible
					choice4.setVisible(false);//Sets the buttons to invisible
					position = "endIt";//Indication of which method is currently running
					mainTextArea.setText("You grab a knife out of the glove compartment and stab yourself with it ending your own life. YOU DIE");//Placement for text
					choice1.setText("Continue");//Display text on button
				}
			public void tryToRun()
				{
					playerPanel.validate();//Refreshes the panel
					playerPanel.repaint();//Tells program that panel needs refreshing
					choice2.setVisible(false);//Sets the buttons to invisible
					choice3.setVisible(false);//Sets the buttons to invisible
					choice4.setVisible(false);//Sets the buttons to invisible
					position = "tryToRun";//Indication of which method is currently running
					mainTextArea.setText("You get out of your car and sprint through the zombies. "
							+ "You are pushing them any and you have almost made it out you get to the end of the herd and haven't been bit. "
							+ "You think you have made it all the way out but out of nowhere a zombie grabs you by the are and bites you.YOU DIE ");//Placement for text
					choice1.setText("Continue");//Display text on button
				}
			public void getoutcont()
				{
					playerPanel.validate();//Refreshes the panel
					playerPanel.repaint();//Tells program that panel needs refreshing
					choice2.setVisible(true);//Sets the buttons to invisible
					choice3.setVisible(false);//Sets the buttons to invisible
					choice4.setVisible(false);//Sets the buttons to invisible
					position = "getoutcont";//Indication of which method is currently running
					mainTextArea.setText("You get out and try to run to the forest. "
							+ "As you are running you you pass many zombies and they start following you. "
							+ "You get into the woods and realize that there is nowhere to go but up. "
							+ "You find a large tree and climb all the way up it. "
							+ "You look down to see that the zombies didn't know where you went and kept walking into the forest. "
							+ "You climb down the tree and start walking towards the road on the road there is only one zombie left. Do you:");//Placement for text
					choice1.setText("Go up and try to kill it");//Display text on button
					choice2.setText("Get back in your car and hit it");//Display text on button
					choice3.setText("");//Display text on button
					choice4.setText("");//Display text on button
				}
			public void hitWithCar()
			{
				playerPanel.validate();//Refreshes the panel
				playerPanel.repaint();//Tells program that panel needs refreshing
				choice2.setVisible(false);//Sets the buttons to invisible
				choice3.setVisible(false);//Sets the buttons to invisible
				choice4.setVisible(false);//Sets the buttons to invisible
				position = "hitWithCar";//Indication of which method is currently running
				mainTextArea.setText("You go back to your car and get in. as you sit down. "
						+ "Out of nowhere a zombie grabs you from the back seat and bites you. YOU DIE");//Placement for text
				choice1.setText("Continue");//Display text on button
				choice2.setText("");//Display text on button
				choice3.setText("");//Display text on button
				choice4.setText("");//Display text on button
			}
			public void oneZombie()
				{
					playerPanel.validate();//Refreshes the panel
					playerPanel.repaint();//Tells program that panel needs refreshing
					choice2.setVisible(true);//Sets the buttons to invisible
					choice3.setVisible(false);//Sets the buttons to invisible
					choice4.setVisible(false);//Sets the buttons to invisible
					position = "oneZombie";//Indication of which method is currently running
					mainTextArea.setText("You walk over to it and you realize that it is your best friend Marty B. "
							+ "You go up to him and then he starts coming at you. As he comes at you you hit him with you (insert weapon) and kill him. "
							+ "When he hits the ground you notice that there is something in his pocket. You reach into his pocket and pull out a key and a note. "
							+ "The note asks you to avenge his death and kill the zombie that killed infected him. "
							+ "The note also says the the zombie is in the town beside the one he lives in and that the zombie will have his shirt tied around his neck. Do you ");//Placement for text
					choice1.setText("Take on the mission ");//Display text on button
					choice2.setText("Not do anything about it and try to stay alive  ");//Display text on button
					choice3.setText("");//Display text on button
					choice4.setText("");//Display text on button
				}
			public void doNothing()
			{
				playerPanel.validate();//Refreshes the panel
				playerPanel.repaint();//Tells program that panel needs refreshing
				choice2.setVisible(false);//Sets the buttons to invisible
				choice3.setVisible(false);//Sets the buttons to invisible
				choice4.setVisible(false);//Sets the buttons to invisible
				position = "doNothing";//Indication of which method is currently running
				mainTextArea.setText("You decide that you don't care about the note and that Marty is not worth avenging. "
						+ "You go back to your car and get in. as you sit down a zombie grabs you from the back seat and bites you. YOU DIE");//Placement for text
				choice1.setText("Continue");//Display text on button
				choice2.setText("");//Display text on button
				choice3.setText("");//Display text on button
				choice4.setText("");//Display text on button
			}
			public void takeMission()
				{
					playerPanel.validate();//Refreshes the panel
					playerPanel.repaint();//Tells program that panel needs refreshing
					choice2.setVisible(true);//Sets the buttons to invisible
					choice3.setVisible(false);//Sets the buttons to invisible
					choice4.setVisible(false);//Sets the buttons to invisible
					position = "takeMission";//Indication of which method is currently running
					mainTextArea.setText("You choose to take on the mission and start walking towards the town beside Marty's town. "
							+ "As you are walking on the road you start to see the town in the distance. "
							+ "You notice that it looks empty but you decide to go in anyways. "
							+ "You go into the town and look down the streets to see a pack of 5 zombies. Do you: ");//Placement for text
					choice1.setText("Go and fight the zombies");//Display text on button
					choice2.setText("Just keep looking for the zombie that killed Marty B");//Display text on button
					choice3.setText("");//Display text on button
					choice4.setText("");//Display text on button
				}
			public void takeMissionCont()
			{
				playerPanel.validate();//Refreshes the panel
				playerPanel.repaint();//Tells program that panel needs refreshing
				choice2.setVisible(true);//Sets the buttons to invisible
				choice3.setVisible(false);//Sets the buttons to invisible
				choice4.setVisible(false);//Sets the buttons to invisible
				position = "takeMissionCont";//Indication of which method is currently running
				mainTextArea.setText("You leave the zombies and look around for the one that killed your friend. "
						+ "You start walking the town and you realize that the town is mostly empty except for just a few zombies. "
						+ "Every zombie you see you look at its neck but don't see Marty's shirt. Just before you are about to give up you hear a roar from inside one of the houses. "
						+ "You look around and see 2 boxes that are locked one contains a weapon and one contains extra health. Do you:");//Placement for text
				choice1.setText("Pick the weapon");//Display text on button
				choice2.setText("Pick the health");//Display text on button
				choice3.setText("");//Display text on button
				choice4.setText("");//Display text on button
			}
			public void healthPick()
			{
				playerPanel.validate();//Refreshes the panel
				playerPanel.repaint();//Tells program that panel needs refreshing
				choice2.setVisible(false);//Sets the buttons to invisible
				choice3.setVisible(false);//Sets the buttons to invisible
				choice4.setVisible(false);//Sets the buttons to invisible
				position = "healthPick";//Indication of which method is currently running
				mainTextArea.setText("You grab your weapon and go into fight the zombie that killed your friend. "
						+ "You see the zombie in the living room but you notice that it is not just any zombie it is a ZOMBIE BEAR. You go to attack it ");//Placement for text
				choice1.setText("FOR MARTY B!!!!");//Display text on button
				choice2.setText("");//Display text on button
				choice3.setText("");//Display text on button
				choice4.setText("");//Display text on button
			}
			public void weaponPick()
			{
				playerPanel.validate();//Refreshes the panel
				playerPanel.repaint();//Tells program that panel needs refreshing
				choice2.setVisible(false);//Sets the buttons to invisible
				choice3.setVisible(false);//Sets the buttons to invisible
				choice4.setVisible(false);//Sets the buttons to invisible
				position = "weaponPick";//Indication of which method is currently running
				mainTextArea.setText("You grab your weapon and go into fight the zombie that killed your friend. "
						+ "You see the zombie in the living room but you notice that it is not just any zombie it is a ZOMBIE BEAR. You go to attack it ");//Placement for text
				choice1.setText("FOR MARTY B!!!!");//Display text on button
				choice2.setText("");//Display text on button
				choice3.setText("");//Display text on button
				choice4.setText("");//Display text on button
			}
			public void bearFight()
			{
				playerPanel.validate();//Refreshes the panel
				playerPanel.repaint();//Tells program that panel needs refreshing
				choice2.setVisible(false);//Sets the buttons to invisible
				choice3.setVisible(false);//Sets the buttons to invisible
				choice4.setVisible(false);//Sets the buttons to invisible
				position = "bearFight";//Indication of which method is currently running
				mainTextArea.setText("Zombie HP: " + zombieHP);//Placement for text
				choice1.setText("Attack with your weapon");//Display text on button
				choice2.setText("");//Display text on button
				choice3.setText("");//Display text on button
				choice4.setText("");//Display text on button
			}
			public void fightZombies()
				{
					playerPanel.validate();//Refreshes the panel
					playerPanel.repaint();//Tells program that panel needs refreshing
					choice2.setVisible(false);//Sets the buttons to invisible
					choice3.setVisible(false);//Sets the buttons to invisible
					choice4.setVisible(false);//Sets the buttons to invisible
					position = "fightZombies";//Indication of which method is currently running
					mainTextArea.setText("You start running at the five zombies and hit the first one with your (insert weapon) in the head. "
							+ "You pull your (insert weapon) out and swing at the next zombie. "
							+ "You keep swinging your weapon around and end up hitting one of the zombies. "
							+ "You try to pull your sword out but it's stuck. The other zombies are coming at you and you keep pulling at your (insert weapon) but it won't come out. "
							+ "You leave your (insert weapon) and try to run away. "
							+ "As you are running you trip over a dead zombie and before you can even get up the three remaining zombies are on top of you. YOU DIE");//Placement for text
					choice1.setText("Continue");//Display text on button
					choice2.setText("");//Display text on button
					choice3.setText("");//Display text on button
					choice4.setText("");//Display text on button
				}
			public void giveup()
				{
					playerPanel.validate();//Refreshes the panel
					playerPanel.repaint();//Tells program that panel needs refreshing
					choice2.setVisible(false);//Sets the buttons to invisible
					choice3.setVisible(false);//Sets the buttons to invisible
					choice4.setVisible(false);//Sets the buttons to invisible
					position = "giveup";//Indication of which method is currently running
					mainTextArea.setText("You decide that there is no point in even trying to stay alive anymore and you decide that you want to end your own life."
							+"You get out of the car and walk towards the herd so they can end it for you. YOU DIE");//Placement for text
					choice1.setText("Continue");//Display text on button
					choice2.setText("");//Display text on button
					choice3.setText("");//Display text on button
					choice4.setText("");//Display text on button
				}
			public void stomp()
			{
				playerPanel.validate();//Refreshes the panel
				playerPanel.repaint();//Tells program that panel needs refreshing
				choice2.setVisible(true);//Sets the buttons to invisible
				choice3.setVisible(true);//Sets the buttons to invisible
				choice4.setVisible(true);//Sets the buttons to invisible
				position = "stomp";//Indication of which method is currently running
				mainTextArea.setText(""
						+""
						+"");//Placement for text
				choice1.setText("");//Display text on button
				choice2.setText("");//Display text on button
				choice3.setText("");//Display text on button
				
				choice4.setText("");//Display text on button
			}
			public void turnaroundcont()
			{
				playerPanel.validate();//Refreshes the panel
				playerPanel.repaint();//Tells program that panel needs refreshing
				choice2.setVisible(true);//Sets the buttons to invisible
				choice3.setVisible(true);//Sets the buttons to invisible
				choice4.setVisible(true);//Sets the buttons to invisible
				position = "turnaroundcont";//Indication of which method is currently running
				mainTextArea.setText(""
						+""
						+"");//Placement for text
				choice1.setText("");//Display text on button
				choice2.setText("");//Display text on button
				choice3.setText("");//Display text on button
				
				choice4.setText("");//Display text on button
			}
			public void getout()
	{
		playerPanel.validate();//Refreshes the panel
		playerPanel.repaint();//Tells program that panel needs refreshing
		choice2.setVisible(true);//Sets the buttons to invisible
		choice3.setVisible(true);//Sets the buttons to invisible
		choice4.setVisible(true);//Sets the buttons to invisible
		position = "getout";//Indication of which method is currently running
		mainTextArea.setText("You hop out of your car and run to the nearby forest."
				+"In the forest you hide behind the trees as you try and make it by the herd without being seen."
				+"Well you are running from tree to tree you end up stepping on a bear trap and scream in pain."
				+"You take the the  bear trap off and notice your scream attracts the attention of the nearby zombies and that they are coming towards you. Do you:");//Placement for text
		choice1.setText("Run as fast as you can and try and get away");//Display text on button
		choice2.setText("Climb the nearby tree and hope the zombies don’t see you");//Display text on button
		choice3.setText("Try and fight your way through the zombies with nothing but your bare hands and a bear trap");//Display text on button
		
		choice4.setText("");//Display text on button
	}
			public void run()
		{
			playerPanel.validate();//Refreshes the panel
			playerPanel.repaint();//Tells program that panel needs refreshing
			choice2.setVisible(true);//Sets the buttons to invisible
			choice3.setVisible(true);//Sets the buttons to invisible
			choice4.setVisible(true);//Sets the buttons to invisible
			position = "run";//Indication of which method is currently running
			mainTextArea.setText("You hop out of your car and run to the nearby forest."
					+"In the forest you hide behind the trees as you try and make it by the herd without being seen."
					+"Well you are running from tree to tree you end up stepping on a bear trap and scream in pain."
					+"You take the the  bear trap off and notice your scream attracts the attention of the nearby zombies and that they are coming towards you. Do you:");//Placement for text
			choice1.setText("Run as fast as you can and try and get away");//Display text on button
			choice2.setText("Climb the nearby tree and hope the zombies don’t see you");//Display text on button
			choice3.setText("Try and fight your way through the zombies with nothing but your bare hands and a bear trap");//Display text on button
			
			choice4.setText("");//Display text on button
		}
			public void climb()
		{
			playerPanel.validate();//Refreshes the panel
			playerPanel.repaint();//Tells program that panel needs refreshing
			choice2.setVisible(true);//Sets the buttons to invisible
			choice3.setVisible(true);//Sets the buttons to invisible
			choice4.setVisible(true);//Sets the buttons to invisible
			position = "climb";//Indication of which method is currently running
			mainTextArea.setText("You hop out of your car and run to the nearby forest."
					+"In the forest you hide behind the trees as you try and make it by the herd without being seen."
					+"Well you are running from tree to tree you end up stepping on a bear trap and scream in pain."
					+"You take the the  bear trap off and notice your scream attracts the attention of the nearby zombies and that they are coming towards you. Do you:");//Placement for text
			choice1.setText("Run as fast as you can and try and get away");//Display text on button
			choice2.setText("Climb the nearby tree and hope the zombies don’t see you");//Display text on button
			choice3.setText("Try and fight your way through the zombies with nothing but your bare hands and a bear trap");//Display text on button
			
			choice4.setText("");//Display text on button
		}
			public void runaway()
			{
				playerPanel.validate();//Refreshes the panel
				playerPanel.repaint();//Tells program that panel needs refreshing
				choice2.setVisible(true);//Sets the buttons to invisible
				choice3.setVisible(true);//Sets the buttons to invisible
				choice4.setVisible(true);//Sets the buttons to invisible
				position = "runaway";//Indication of which method is currently running
				mainTextArea.setText("You start running away from the zombies but because of the wounds you have received from the bear trap the zombies keep getting closer and closer as you try and get away."
						+"You see an  old cottage as you are running. Do you:");//Placement for text
				choice1.setText("Run inside the cottage");//Display text on button
				choice2.setText("Run past the cottage");//Display text on button
				choice3.setText("Try to see inside the cottage through the windows");//Display text on button
				
				choice4.setText("");//Display text on button
			}
			public void incottage()
				{
					playerPanel.validate();//Refreshes the panel
					playerPanel.repaint();//Tells program that panel needs refreshing
					choice2.setVisible(true);//Sets the buttons to invisible
					choice3.setVisible(true);//Sets the buttons to invisible
					choice4.setVisible(true);//Sets the buttons to invisible
					position = "incottage";//Indication of which method is currently running
					mainTextArea.setText("You run inside the cottage slamming the door behind you locking the door and collapsing at it in pain."
							+"You look around and the cottage looks completely empty."
							+"You try to get up to search the cottage but you end up passing out from too much blood loss."
							+"You wake up and you are in a bed with your leg bandaged."
							+"You try to get up but it hurts to much to stand."
							+"You see that a person is coming to the door but you can't see who it is. Do you");//Placement for text
					choice1.setText("Grab the pair of scissors that are beside your bed and throw them at the person");//Display text on button
					choice2.setText("Just lay in the bed and hope the person is friendly.");//Display text on button
					choice3.setText("");//Display text on button
					
					choice4.setText("");//Display text on button
				}
			public void scissors()
					{
						playerPanel.validate();//Refreshes the panel
						playerPanel.repaint();//Tells program that panel needs refreshing
						choice2.setVisible(true);//Sets the buttons to invisible
						choice3.setVisible(true);//Sets the buttons to invisible
						choice4.setVisible(true);//Sets the buttons to invisible
						position = "scissors";//Indication of which method is currently running
						mainTextArea.setText("You grab the scissors and get ready to throw them. "
								+"As the person is walking you throw the scissors before you can see his face. "
								+"The scissors land right in his chest."
								+"You think it was a great throw until you notice that the man was your best friend Marty B."
								+"You see Marty fall to the ground in pain. You go into deep depression and commit suicide. YOU DIE.");//Placement for text
					}
			public void laydown()
					{
						playerPanel.validate();//Refreshes the panel
						playerPanel.repaint();//Tells program that panel needs refreshing
						choice2.setVisible(true);//Sets the buttons to invisible
						choice3.setVisible(true);//Sets the buttons to invisible
						choice4.setVisible(true);//Sets the buttons to invisible
						position = "laydown";//Indication of which method is currently running
						mainTextArea.setText("You are lying in the bed as the unknown person comes back."
								+"You stare at the door waiting for the person to walk in"
								+"as he walks in you notice that is it your best friend Marty B. ");//Placement for text
						choice1.setText("");//Display text on button
						choice2.setText("");//Display text on button
						choice3.setText("");//Display text on button
						
						choice4.setText("");//Display text on button
					}
			public void pastcottage()
				{
					playerPanel.validate();//Refreshes the panel
					playerPanel.repaint();//Tells program that panel needs refreshing
					choice2.setVisible(true);//Sets the buttons to invisible
					choice3.setVisible(true);//Sets the buttons to invisible
					choice4.setVisible(true);//Sets the buttons to invisible
					position = "pastcottage";//Indication of which method is currently running
					mainTextArea.setText("ou run past the cottage and try to outrun the zombies even though you are bleeding from your wounds."
							+"You keep running but the pain in your leg is to great to keep moving on in. you end up collapsing to the ground in pain and get overtaken by zombies. YOU DIE");//Placement for text
				}
			public void seecottage()
				{
					playerPanel.validate();//Refreshes the panel
					playerPanel.repaint();//Tells program that panel needs refreshing
					choice2.setVisible(true);//Sets the buttons to invisible
					choice3.setVisible(true);//Sets the buttons to invisible
					choice4.setVisible(true);//Sets the buttons to invisible
					position = "seecottage";//Indication of which method is currently running
					mainTextArea.setText("You run to the window to try and see what's inside while the zombies are still after you and you see that the house looks like it's abandoned so you start walking to the door."
							+"As you are going to the door a zombie crawls out from under the cottage knocking you to the ground and you hit your head off of a rock. YOU DIE");//Placement for text
				}
			public void climbtree()
			{
				playerPanel.validate();//Refreshes the panel
				playerPanel.repaint();//Tells program that panel needs refreshing
				choice2.setVisible(true);//Sets the buttons to invisible
				choice3.setVisible(true);//Sets the buttons to invisible
				choice4.setVisible(true);//Sets the buttons to invisible
				position = "climbtree";//Indication of which method is currently running
				mainTextArea.setText("You climb up the tree as high as you can and sit on one of the larger branches being as quiet as you can."
						+"The herd walk past you and doesn't even notice that you’re there");//Placement for text
				choice1.setText("");//Display text on button
				choice2.setText("");//Display text on button
				choice3.setText("");//Display text on button
				
				choice4.setText("");//Display text on button
			}
			public void beartrap()
			{
				playerPanel.validate();//Refreshes the panel
				playerPanel.repaint();//Tells program that panel needs refreshing
				choice2.setVisible(true);//Sets the buttons to invisible
				choice3.setVisible(true);//Sets the buttons to invisible
				choice4.setVisible(true);//Sets the buttons to invisible
				position = "climbtree";//Indication of which method is currently running
				mainTextArea.setText("You get ready to fight as the zombies are coming closer and as the first zombie gets to you you hit it as hard as you can with the trap."
						+"The trap gets stuck in the zombie and you can't get it out to fight. "
						+"You leave it and start fighting with your hands throwing zombies to the ground as they come."
						+"As you are fighting you notice that the zombies have surrounded you and there is no way out. "
						+"You hit one zombie but another tackles you to the ground and then they are all on top of you and they start eating you alive. YOU DIE ");//Placement for text
			}
			public void fightzombie()
		{
			playerPanel.validate();//Refreshes the panel
			playerPanel.repaint();//Tells program that panel needs refreshing
			choice2.setVisible(true);//Sets the buttons to invisible
			choice3.setVisible(true);//Sets the buttons to invisible
			choice4.setVisible(true);//Sets the buttons to invisible
			position = "climbtree";//Indication of which method is currently running
			mainTextArea.setText("You get out of your truck and look around for a weapon to help you fight off the zombies. On the ground you see three items (insert images for the items)");
					choice1.setText("A small knife that is covered in blood and stuck to a nearby tree");//Display text on button
					choice2.setText("A handgun that is in a bush but you don’t know if it is loaded");//Display text on button
					choice3.setText("A old broom stick that is sharpened at one end.");//Display text on button
					
					choice4.setText("");//Display text on button
		}
			public void knife()
			{
				playerPanel.validate();//Refreshes the panel
				playerPanel.repaint();//Tells program that panel needs refreshing
				choice2.setVisible(true);//Sets the buttons to invisible
				choice3.setVisible(true);//Sets the buttons to invisible
				choice4.setVisible(true);//Sets the buttons to invisible
				position = "knife";//Indication of which method is currently running
				mainTextArea.setText("You run as fast as you can to the tree to pull the knife out but you are seen by one of the nearby zombies."
						+"You try to pull the knife out but it is stuck so you pull as hard as you can ripping the knife out but as you do your arm swings back and hitting one of the zombies in the head with a knife."
						+ "As you kill one zombie another zombie crawling on the ground bites you leg turning you into a zombie you killing you. YOU DIE");
			}
			public void gun()
			{
				playerPanel.validate();//Refreshes the panel
				playerPanel.repaint();//Tells program that panel needs refreshing
				choice2.setVisible(true);//Sets the buttons to invisible
				choice3.setVisible(true);//Sets the buttons to invisible
				choice4.setVisible(true);//Sets the buttons to invisible
				position = "gun";//Indication of which method is currently running
				mainTextArea.setText("You run to the bush to grab the gun but as you get closer you realize that the gun is in the hands of a dead zombie. "
						+ " You end up peeling the gun out of the dead man's hand and check to see if there are any bullets in the gun. the gun ends up only having 1 bullet. Do you");
				choice1.setText("Put the gun in your mouth and end it before the zombies can");//Display text on button
				choice2.setText("Try and run through the herd and only shoot if you need to ");//Display text on button
				choice3.setText("");//Display text on button
				
				choice4.setText("");//Display text on button
			}
			public void die()
				{
					playerPanel.validate();//Refreshes the panel
					playerPanel.repaint();//Tells program that panel needs refreshing
					choice2.setVisible(true);//Sets the buttons to invisible
					choice3.setVisible(true);//Sets the buttons to invisible
					choice4.setVisible(true);//Sets the buttons to invisible
					position = "die";//Indication of which method is currently running
					mainTextArea.setText("You die");
					dead();
				}
			public void pastherd()
					{
						playerPanel.validate();//Refreshes the panel
						playerPanel.repaint();//Tells program that panel needs refreshing
						choice2.setVisible(true);//Sets the buttons to invisible
						choice3.setVisible(true);//Sets the buttons to invisible
						choice4.setVisible(true);//Sets the buttons to invisible
						position = "pastherd";//Indication of which method is currently running
						mainTextArea.setText("You run as fast as you can at the hurd dodging zombies left and right"
								+ " You are in the middle of the hurd and look for a way out but you are surrounded by zombies you shoot one but as you do another one bites you YOU DIE ");
					}
			public void broom()
			{
				playerPanel.validate();//Refreshes the panel
				playerPanel.repaint();//Tells program that panel needs refreshing
				choice2.setVisible(true);//Sets the buttons to invisible
				choice3.setVisible(true);//Sets the buttons to invisible
				choice4.setVisible(true);//Sets the buttons to invisible
				position = "broom";//Indication of which method is currently running
				mainTextArea.setText("You run to the bush to grab the gun but as you get closer you realize that the gun is in the hands of a dead zombie. "
						+ " You end up peeling the gun out of the dead man's hand and check to see if there are any bullets in the gun. the gun ends up only having 1 bullet. Do you");
			}
			public void fightThroughZombie()
			{
				playerPanel.validate();//Refreshes the panel
				playerPanel.repaint();//Tells program that panel needs refreshing
				choice2.setVisible(true);//Sets the buttons to invisible
				choice3.setVisible(true);//Sets the buttons to invisible
				choice4.setVisible(false);//Sets the buttons to invisible
				position = "fightThroughZombie";//Indication of which method is currently running
				mainTextArea.setText("If you choose D, You get out of your truck and look around for a weapon to help you fight off the zombies. "
						+ "On the ground you see three items: ");//Placement for text
				choice1.setText("A small knife that is covered in blood and stuck to a nearby tree");//Display text on button
				choice2.setText("A handgun that is in a bush but you don’t know if it is loaded ");//Display text on button
				choice3.setText("A old broom stick that is sharpened at one end.");//Display text on button
				
				choice4.setText("");//Display text on button
			}
			public void smallKnife()
			{
				playerPanel.validate();//Refreshes the panel
				playerPanel.repaint();//Tells program that panel needs refreshing
				choice2.setVisible(false);//Sets the buttons to invisible
				choice3.setVisible(false);//Sets the buttons to invisible
				choice4.setVisible(false);//Sets the buttons to invisible
				position = "smallKnife";//Indication of which method is currently running
				mainTextArea.setText("You run as fast as you can to the tree to pull the knife out but you are seen by one of the nearby zombies. "
						+ "You try to pull the knife out but it is stuck so you pull as hard as you can ripping the knife out but as you do your arm swings back and hitting one of the zombies in the head with a knife. "
						+ "As you kill one zombie another zombie crawling on the ground bites you leg turning you into a zombie you killing you. YOU DIE ");//Placement for text
				choice1.setText("Continue");//Display text on button
				choice2.setText("");//Display text on button
				choice3.setText("");//Display text on button
				
				choice4.setText("");//Display text on button
			}
			public void handgun()
			{
				playerPanel.validate();//Refreshes the panel
				playerPanel.repaint();//Tells program that panel needs refreshing
				choice2.setVisible(true);//Sets the buttons to invisible
				choice3.setVisible(false);//Sets the buttons to invisible
				choice4.setVisible(false);//Sets the buttons to invisible
				position = "handgun";//Indication of which method is currently running
				mainTextArea.setText("A handgun that is in a bush but you don’t know if it is loaded You run to the bush to grab the gun but as you get closer you realize that the gun is in the hands of a dead zombie. "
						+ "You end up peeling the gun out of the dead man's hand and check to see if there are any bullets in the gun. The gun ends up only having 1 bullet. Do you:  ");//Placement for text
				choice1.setText("Put the gun in your mouth and end it before the zombies can");//Display text on button
				choice2.setText("Try and run through the herd and only shoot if you need to");//Display text on button
				choice3.setText("");//Display text on button
				
				choice4.setText("");//Display text on button
			}
			public void suicide()
			{
				playerPanel.validate();//Refreshes the panel
				playerPanel.repaint();//Tells program that panel needs refreshing
				choice2.setVisible(false);//Sets the buttons to invisible
				choice3.setVisible(false);//Sets the buttons to invisible
				choice4.setVisible(false);//Sets the buttons to invisible
				position = "suicide";//Indication of which method is currently running
				mainTextArea.setText("You pulled the trigger, YOU DIE");//Placement for text
				choice1.setText("Continue");//Display text on button
				choice2.setText("");//Display text on button
				choice3.setText("");//Display text on button
				
				choice4.setText("");//Display text on button
			}
			public void runthroughhurd()
			{
				playerPanel.validate();//Refreshes the panel
				playerPanel.repaint();//Tells program that panel needs refreshing
				choice2.setVisible(false);//Sets the buttons to invisible
				choice3.setVisible(false);//Sets the buttons to invisible
				choice4.setVisible(false);//Sets the buttons to invisible
				position = "handgun";//Indication of which method is currently running
				mainTextArea.setText("Try and run through the herd and only shoot if you need to You run as fast as you can at the hurd dodging zombies left and right. "
						+ "You are in the middle of the hurd and look for a way out but you are surrounded by zombies you shoot one but as you do another one bites you YOU DIE ");//Placement for text
				choice1.setText("Continue");//Display text on button
				choice2.setText("");//Display text on button
				choice3.setText("");//Display text on button
				
				choice4.setText("");//Display text on button
			}
			public void broomStick()
			{
				playerPanel.validate();//Refreshes the panel
				playerPanel.repaint();//Tells program that panel needs refreshing
				choice2.setVisible(false);//Sets the buttons to invisible
				choice3.setVisible(false);//Sets the buttons to invisible
				choice4.setVisible(false);//Sets the buttons to invisible
				position = "broomStick";//Indication of which method is currently running
				mainTextArea.setText("You grab the broomstick and start moving towards the herd of zombies. "
						+ "You kill the first one that comes at you and then the second. "
						+ "Then you start running through the zombies killing as many as you can as you go through but the stick ends up breaking as you are going and you are surrounded by zombies. "
						+ "You look around for help but you don't see anyone or anything and you realize that it is over. YOU DIE.");//Placement for text
				choice1.setText("Continue");//Display text on button
				choice2.setText("");//Display text on button
				choice3.setText("");//Display text on button
				
				choice4.setText("");//Display text on button
			}
			public void dead()
{
	playerPanel.validate();//Refreshes the panel
	playerPanel.repaint();//Tells program that panel needs refreshing
	choice2.setVisible(true);//Sets the buttons to invisible
	choice3.setVisible(false);//Sets the buttons to invisible
	choice4.setVisible(false);//Sets the buttons to invisible
	position = "dead";//Indication of which method is currently running
	mainTextArea.setText("Would you like to play again?");//Placement for text
	choice1.setText("Yes");//Display text on button
	choice2.setText("No");//Display text on button
	choice3.setText("");//Display text on button
	
	choice4.setText("");//Display text on button 
}
			
	public class TitleScreenHandler implements ActionListener{//Interface for receiving an action event (Button press)
		
		public void actionPerformed(ActionEvent event){//Indicates that an action has occurred
			
			createGameScreen();//This is called after action has been detected
	  }
   }
	public class ChoiceHandler implements ActionListener{//Interface for receiving an action event (Button press)
		
		public void actionPerformed(ActionEvent event){//Indicates that an action has occurred
			
			String yourChoice = event.getActionCommand();//Recognizes which choice button is clicked
			
				switch(position){//Determines which method is being processed
					case "mainScreen"://Indicates which method is being processed
						switch(yourChoice){//Determines which choice button was clicked
						case "c1": mainScreencont(); break;//Result of choice 1 button click
						} 
						break;
					case "mainScreencont"://Indicates which method is being processed
						switch(yourChoice){//Determines which choice button was clicked
						case "c1": drivetru(); break;//Result of choice 1 button click
						case "c2": turnaround();break;//Result of choice 2 button click
						case "c3": fightThroughZombie();break;//Result of choice 3 button click
						case "c4": break;//Result of choice 4 button click
						} 
						break;
					case "drivetru"://Indicates which method is being processed
						switch(yourChoice){//Determines which choice button was clicked
						case "c1": drivecont(); break;//Result of choice 1 button click
						case "c2": holdup();break;//Result of choice 2 button click
						case "c3": walk();break;//Result of choice 3 button click
						case "c4": parts();break;//Result of choice 4 button click
						} 
						break;
					case "parts"://Indicates which method is being processed
						switch(yourChoice){//Determines which choice button was clicked
						case "c1": runFromZombies(); break;//Result of choice 1 button click
						case "c2": holdup();break;//Result of choice 2 button click
						case "c3": break;//Result of choice 3 button click
						case "c4": break;//Result of choice 4 button click
						} 
						break;
					case "runFromZombies"://Indicates which method is being processed
						switch(yourChoice){//Determines which choice button was clicked
						case "c1": dead(); break;//Result of choice 1 button click
						case "c2": break;//Result of choice 2 button click
						case "c3": break;//Result of choice 3 button click
						case "c4": break;//Result of choice 4 button click
						} 
						break;
					case "getInCarAndHide"://Indicates which method is being processed
						switch(yourChoice){//Determines which choice button was clicked
						case "c1": dead(); break;//Result of choice 1 button click
						case "c2": break;//Result of choice 2 button click
						case "c3": break;//Result of choice 3 button click
						case "c4": break;//Result of choice 4 button click
						} 
						break;
					case "drivecont"://Indicates which method is being processed
						switch(yourChoice){//Determines which choice button was clicked
						case "c1": dead();break;//Result of choice 1 button click
						case "c2": dead();break;//Result of choice 2 button click
						} 
						break;
					case "holdup"://Indicates which method is being processed
						switch(yourChoice){//Determines which choice button was clicked
						case "c1": dead();break;//Result of choice 1 button click
						case "c2": dead();break;//Result of choice 2 button click
						}
						break;
					case "walk"://Indicates which method is being processed
						switch(yourChoice){//Determines which choice button was clicked
						case "c1": walkcont(); break;//Result of choice 1 button click
						case "c2": findfriend();break;//Result of choice 2 button click
						}
						break;
					case "findfriend"://Indicates which method is being processed
						switch(yourChoice){//Determines which choice button was clicked
						case "c1": pickUpChair();break;//Result of choice 1 button click
						case "c2": freezeUp();break;//Result of choice 2 button click
						}
						break;
					case "pickUpChair"://Indicates which method is being processed
						switch(yourChoice){//Determines which choice button was clicked
						case "c1": dead (); break;//Result of choice 1 button click
						case "c2": break;//Result of choice 2 button click
						}
						break;
					case "freezeUp"://Indicates which method is being processed
						switch(yourChoice){//Determines which choice button was clicked
						case "c1": dead (); break;//Result of choice 1 button click
						case "c2": break;//Result of choice 2 button click
						}
						break;
					case "walkcont"://Indicates which method is being processed
						switch(yourChoice){//Determines which choice button was clicked
						case "c1": killYourFriend(); break;//Result of choice 1 button click
						case "c2": runAwayMarty();break;//Result of choice 2 button click
						}
						break;
					case "killYourFriend"://Indicates which method is being processed
						switch(yourChoice){//Determines which choice button was clicked
						case "c1": fightZombie1(); break;//Result of choice 1 button click
						case "c2": lookForZombie();break;//Result of choice 2 button click
						}
						break;
					case "fightZombie1"://Indicates which method is being processed
						switch(yourChoice){//Determines which choice button was clicked
						case "c1": dead(); break;//Result of choice 1 button click
				        }
						break;
					case "lookForZombie"://Indicates which method is being processed
						switch(yourChoice){//Determines which choice button was clicked
						case "c1": pickWeapon();break;//Result of choice 1 button click
						case "c2": pickHealth(); break;//Result of choice 2 button click
						}
						break;
					case "pickWeapon"://Indicates which method is being processed
						switch(yourChoice){//Determines which choice button was clicked
						case "c1": playerAttack ();break;//Result of choice 1 button click
						case "c2": break;//Result of choice 2 button click
						}
						break;
					case "pickHealth"://Indicates which method is being processed
						switch(yourChoice){//Determines which choice button was clicked
						case "c1": playerAttack ();break;//Result of choice 1 button click
						case "c2": break;//Result of choice 2 button click
						}
						break;
					case "runAwayMarty"://Indicates which method is being processed
						switch(yourChoice){//Determines which choice button was clicked
						case "c1": dead(); break;//Result of choice 1 button click
				        }
						break;
					case "turnaround"://Indicates which method is being processed
						switch(yourChoice){//Determines which choice button was clicked
						case "c1": speed(); break;//Result of choice 1 button click
						case "c2": getOutHerd();break;//Result of choice 2 button click
						case "c3": turnaroundcont();break;//Result of choice 3 button click
						case "c4": break;//Result of choice 4 button click
						} 
						break;
					case "getOutHerd"://Indicates which method is being processed
						switch(yourChoice){//Determines which choice button was clicked
						case "c1": getOutHerdCont(); break;//Result of choice 1 button click
						case "c2": attackZombie();break;//Result of choice 2 button click
						case "c3": break;//Result of choice 3 button click
						case "c4": break;//Result of choice 4 button click
						} 
						break;
					case "attackZombie"://Indicates which method is being processed
						switch(yourChoice){//Determines which choice button was clicked
						case "c1": fightZombies();break;//Result of choice 1 button click
						case "c2": takeMissionCont();break;//Result of choice 2 button click
						case "c3": break;//Result of choice 3 button click
						case "c4": break;//Result of choice 4 button click
						} 
						break;
					case "getOutHerdCont"://Indicates which method is being processed
						switch(yourChoice){//Determines which choice button was clicked
						case "c1": dead(); break;//Result of choice 1 button click
						case "c2": break;//Result of choice 2 button click
						case "c3": break;//Result of choice 3 button click
						case "c4": break;//Result of choice 4 button click
						} 
						break;
					case "speed"://Indicates which method is being processed
						switch(yourChoice){//Determines which choice button was clicked
						case "c1": drivetrucont(); break;//Result of choice 1 button click
						case "c2": getoutcont();break;//Result of choice 2 button click
						case "c3": giveup();break;//Result of choice 3 button click
						case "c4": break;//Result of choice 4 button click
						}
						break;
					case "giveup"://Indicates which method is being processed
						switch(yourChoice){//Determines which choice button was clicked
						case "c1": dead(); break;//Result of choice 1 button click
						case "c2": break;//Result of choice 2 button click
						case "c3": break;//Result of choice 3 button click
						case "c4": break;//Result of choice 4 button click
						}
						break;
					case "getoutcont"://Indicates which method is being processed
						switch(yourChoice){//Determines which choice button was clicked
						case "c1": oneZombie(); break;//Result of choice 1 button click 
						case "c2": hitWithCar();break;//Result of choice 2 button click
						case "c3": break;//Result of choice 3 button click
						case "c4": break;//Result of choice 4 button click
						}
						break;
					case "hitWithCar"://Indicates which method is being processed
						switch(yourChoice){//Determines which choice button was clicked
						case "c1": dead(); break;//Result of choice 1 button click 
						case "c2": break;//Result of choice 2 button click
						case "c3": break;//Result of choice 3 button click
						case "c4": break;//Result of choice 4 button click
						}
						break;
					case "oneZombie"://Indicates which method is being processed
						switch(yourChoice){//Determines which choice button was clicked
						case "c1": takeMission(); break;//Result of choice 1 button click
						case "c2": doNothing(); break;//Result of choice 2 button click
						case "c3": break;//Result of choice 3 button click
						case "c4": break;//Result of choice 4 button click
						}
						break;
					case "doNothing"://Indicates which method is being processed
						switch(yourChoice){//Determines which choice button was clicked
						case "c1": dead(); break;//Result of choice 1 button click
						case "c2": break;//Result of choice 2 button click
						case "c3": break;//Result of choice 3 button click
						case "c4": break;//Result of choice 4 button click
						}
						break;
					case "takeMission"://Indicates which method is being processed
						switch(yourChoice){//Determines which choice button was clicked
						case "c1": fightZombies();break;//Result of choice 1 button click
						case "c2": takeMissionCont();break;//Result of choice 2 button click
						case "c3": break;//Result of choice 3 button click
						case "c4": break;//Result of choice 4 button click
						}
						break;
					case "takeMissionCont"://Indicates which method is being processed
						switch(yourChoice){//Determines which choice button was clicked
						case "c1": healthPick();break;//Result of choice 1 button click
						case "c2": weaponPick();break;//Result of choice 2 button click
						case "c3": break;//Result of choice 3 button click
						case "c4": break;//Result of choice 4 button click
						}
						break;
					case "healthPick"://Indicates which method is being processed
						switch(yourChoice){//Determines which choice button was clicked
						case "c1": bearFight();break;//Result of choice 1 button click
						case "c2": break;//Result of choice 2 button click
						case "c3": break;//Result of choice 3 button click
						case "c4": break;//Result of choice 4 button click
						}
						break;
					case "weaponPick"://Indicates which method is being processed
						switch(yourChoice){//Determines which choice button was clicked
						case "c1": bearFight();break;//Result of choice 1 button click
						case "c2": break;//Result of choice 2 button click
						case "c3": break;//Result of choice 3 button click
						case "c4": break;//Result of choice 4 button click
						}
						break;
					case "bearFight"://Indicates which method is being processed
						switch(yourChoice){//Determines which choice button was clicked
						case "c1": playerAttack();break;//Result of choice 1 button click
						case "c2": break;//Result of choice 2 button click
						case "c3": break;//Result of choice 3 button click
						case "c4": break;//Result of choice 4 button click
						}
						break;
					case "fightZombies"://Indicates which method is being processed
						switch(yourChoice){//Determines which choice button was clicked
						case "c1": dead();break;//Result of choice 1 button click
						case "c2": break;//Result of choice 2 button click
						case "c3": break;//Result of choice 3 button click
						case "c4": break;//Result of choice 4 button click
						}
						break;
					case "drivetrucont"://Indicates which method is being processed
						switch(yourChoice){//Determines which choice button was clicked
						case "c1": endIt(); break;//Result of choice 1 button click
						case "c2": tryToRun();break;//Result of choice 2 button click
						case "c3": break;//Result of choice 3 button click
						case "c4": break;//Result of choice 4 button click
						}
						break;
					case "endIt"://Indicates which method is being processed
						switch(yourChoice){//Determines which choice button was clicked
						case "c1": dead(); break;//Result of choice 1 button click//5745 7183 97 123465 bmo 
						case "c2": break;//Result of choice 2 button click
						case "c3": break;//Result of choice 3 button click
						case "c4": break;//Result of choice 4 button click
						}
						break;
					case "tryToRun"://Indicates which method is being processed
						switch(yourChoice){//Determines which choice button was clicked
						case "c1": dead(); break;//Result of choice 1 button click//5745 7183 97 123465 bmo 
						case "c2": break;//Result of choice 2 button click
						case "c3": break;//Result of choice 3 button click
						case "c4": break;//Result of choice 4 button click
						}
						break;
					
					case "dead"://Indicates which method is being processed
						switch(yourChoice){//Determines which choice button was clicked
						case "c1": mainScreen();break;//Result of choice 1 button click
						case "c2": System.exit(0);break;//Result of choice 2 button click
						}
						break;
		
					case "fight"://Indicates which method is being processed
						switch(yourChoice){//Determines which choice button was clicked
						case "c1": playerAttack(); break;//Result of choice 1 button click
						case "c2": break;//Result of choice 2 button click
						case "c3": break;//Result of choice 3 button click
						case "c4": break;//Result of choice 4 button click
						}
						break;
					case "playerAttack"://Indicates which method is being processed
						switch(yourChoice){//Determines which choice button was clicked
						case "c1": 
							if(zombieHP<1){//Checks if zombie's health is less than 1
								win();//If health less than one, then win method is called
							}
							else{
								zombieAttack();//If health more than one, then zombie attack method is called
								}
								break;//Result of choice 1 button click
						case "c2": break;//Result of choice 2 button click
						case "c3": break;//Result of choice 3 button click
						case "c4": break;//Result of choice 4 button click
						}
						break;
					case "zombieAttack"://Indicates which method is being processed
						switch(yourChoice){//Determines which choice button was clicked
						case "c1":  
							if(playerHP<1){//Checks if player's health is less than 1
								dead();//If health less than one, then lose method is called
							}
							else{
								bearFight();//If health more than one, then playerattack method is called
							}
								break;//Result of choice 1 button click
						case "c2": break;//Result of choice 2 button click
						case "c3": break;//Result of choice 3 button click
						case "c4": break;//Result of choice 4 button click
						}
						break;
					case "win"://Indicates which method is being processed
						switch(yourChoice){//Determines which choice button was clicked
						case "c1": victory();break;//Result of choice 1 button click
						case "c2": break;//Result of choice 2 button click
						case "c3": break;//Result of choice 3 button click
						case "c4": break;//Result of choice 4 button click
						}
						break;
					case "fightThroughZombie"://Indicates which method is being processed
						switch(yourChoice){//Determines which choice button was clicked
						case "c1": smallKnife();break;//Result of choice 1 button click//5745 7183 97 123465 bmo 
						case "c2": handgun();break;//Result of choice 2 button click
						case "c3": broomStick();break;//Result of choice 3 button click
						case "c4": break;//Result of choice 4 button click
						}
						break;
					case "smallKnife"://Indicates which method is being processed
						switch(yourChoice){//Determines which choice button was clicked
						case "c1": dead();break;//Result of choice 1 button click//5745 7183 97 123465 bmo 
						case "c2": break;//Result of choice 2 button click
						case "c3": break;//Result of choice 3 button click
						case "c4": break;//Result of choice 4 button click
						}
						break;
					case "handgun"://Indicates which method is being processed
						switch(yourChoice){//Determines which choice button was clicked
						case "c1": suicide();break;//Result of choice 1 button click//5745 7183 97 123465 bmo 
						case "c2": runthroughhurd();break;//Result of choice 2 button click
						case "c3": break;//Result of choice 3 button click
						case "c4": break;//Result of choice 4 button click
						}
						break;
					case "suicide"://Indicates which method is being processed
						switch(yourChoice){//Determines which choice button was clicked
						case "c1": dead();break;//Result of choice 1 button click//5745 7183 97 123465 bmo 
						case "c2": break;//Result of choice 2 button click
						case "c3": break;//Result of choice 3 button click
						case "c4": break;//Result of choice 4 button click
						}
						break;
					case "runthroughhurd"://Indicates which method is being processed
						switch(yourChoice){//Determines which choice button was clicked
						case "c1": dead();break;//Result of choice 1 button click//5745 7183 97 123465 bmo 
						case "c2": break;//Result of choice 2 button click
						case "c3": break;//Result of choice 3 button click
						case "c4": break;//Result of choice 4 button click
						}
						break;
					case "broomStick"://Indicates which method is being processed
						switch(yourChoice){//Determines which choice button was clicked
						case "c1": dead();break;//Result of choice 1 button click//5745 7183 97 123465 bmo 
						case "c2": break;//Result of choice 2 button click
						case "c3": break;//Result of choice 3 button click
						case "c4": break;//Result of choice 4 button click
						}
						break;
				}
			}
		}
	}

import javax.swing.*;
import java.awt.*;
import java.awt.event.*;
import java.util.Scanner;

public class RadioButtonDemo extends JFrame implements ActionListener {

    private JRadioButton bird, cat, dog, rabbit, pig;
    private JLabel imageLabel;
    private String userName;

    public RadioButtonDemo(String name) {

        userName = name;

        setTitle("Pet Selector");
        setSize(700,500);
        setLayout(new BorderLayout());
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);

        JPanel leftPanel = new JPanel();
        leftPanel.setLayout(new GridLayout(5,1));

        bird = new JRadioButton("Bird");
        cat = new JRadioButton("Cat");
        dog = new JRadioButton("Dog");
        rabbit = new JRadioButton("Rabbit");
        pig = new JRadioButton("Pig");

        ButtonGroup group = new ButtonGroup();
        group.add(bird);
        group.add(cat);
        group.add(dog);
        group.add(rabbit);
        group.add(pig);

        bird.addActionListener(this);
        cat.addActionListener(this);
        dog.addActionListener(this);
        rabbit.addActionListener(this);
        pig.addActionListener(this);

        leftPanel.add(bird);
        leftPanel.add(cat);
        leftPanel.add(dog);
        leftPanel.add(rabbit);
        leftPanel.add(pig);

        imageLabel = new JLabel();
        imageLabel.setHorizontalAlignment(JLabel.CENTER);

        add(leftPanel, BorderLayout.WEST);
        add(imageLabel, BorderLayout.CENTER);

        setVisible(true);
    }

    @Override
    public void actionPerformed(ActionEvent e) {

        String pet = "";
        String image = "";

        if (bird.isSelected()) {
            pet = "Bird";
            image = "images/bird.jpg";
        }

        if (cat.isSelected()) {
            pet = "Cat";
            image = "images/cat.jpg";
        }

        if (dog.isSelected()) {
            pet = "Dog";
            image = "images/dog.jpg";
        }

        if (rabbit.isSelected()) {
            pet = "Rabbit";
            image = "images/rabbit.jpg";
        }

        if (pig.isSelected()) {
            pet = "Pig";
            image = "images/pig.jpg";
        }

        ImageIcon icon = new ImageIcon(image);

        Image img = icon.getImage().getScaledInstance(350,300,Image.SCALE_SMOOTH);

        imageLabel.setIcon(new ImageIcon(img));

        JOptionPane.showMessageDialog(this,
                "Hello " + userName + "\nYou selected " + pet);
    }

    public static void main(String[] args) {

        Scanner input = new Scanner(System.in);

        System.out.print("Enter your name: ");

        String name = input.nextLine();

        SwingUtilities.invokeLater(() -> new RadioButtonDemo(name));

        input.close();
    }
}

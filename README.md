using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows.Forms;

namespace KrestikiNoliki
{
    public partial class Form1 : Form
    {
        public Form1()
        {
            InitializeComponent();
            button2.Enabled = false;
            pictureBox1.Image = Properties.Resources._4;
           
        }

        private void button1_Click(object sender, EventArgs e)
        {
          
            Graphics g = pictureBox1.CreateGraphics();

            if (radioButton2.Checked == true)
            {
                pictureBox1.Image = Properties.Resources._4х4;
                label2.Text = "Ходят : Крестики";
                button1.Enabled = false;
                button2.Enabled = true;
                radioButton1.Enabled = false;
                radioButton2.Enabled = false;
                radioButton3.Enabled = false;
                checkBox1.Enabled = false;
                g.DrawLine(new Pen(Brushes.Black, 2), new Point(pictureBox1.Width / 4, 0), new Point(pictureBox1.Width / 4, pictureBox1.Height));
                g.DrawLine(new Pen(Brushes.Black, 2), new Point((pictureBox1.Width / 4)*2, 0), new Point((pictureBox1.Width / 4)*2, pictureBox1.Height));
                g.DrawLine(new Pen(Brushes.Black, 2), new Point((pictureBox1.Width / 4) * 3, 0), new Point((pictureBox1.Width / 4) * 3, pictureBox1.Height));
                g.DrawLine(new Pen(Brushes.Black, 2), new Point(0, pictureBox1.Height / 4), new Point(pictureBox1.Width, pictureBox1.Height / 4));
                g.DrawLine(new Pen(Brushes.Black, 2), new Point(0, (pictureBox1.Height / 4) * 2), new Point(pictureBox1.Width, (pictureBox1.Height / 4) * 2));
                g.DrawLine(new Pen(Brushes.Black, 2), new Point(0, (pictureBox1.Height / 4) * 3), new Point(pictureBox1.Width, (pictureBox1.Height / 4) * 3));
                return;
            }
            if (radioButton1.Checked == true)
            {
                pictureBox1.Image = Properties.Resources._3х3;
                label2.Text = "Ходят : Крестики";
                button1.Enabled = false;
                button2.Enabled = true;
                radioButton1.Enabled = false;
                radioButton2.Enabled = false;
                radioButton3.Enabled = false;
                checkBox1.Enabled = false;
                g.DrawLine(new Pen(Brushes.Black, 2), new Point((pictureBox1.Width / 3) * 2, 0), new Point((pictureBox1.Width / 3) * 2, pictureBox1.Height));
                g.DrawLine(new Pen(Brushes.Black, 2), new Point(pictureBox1.Width / 3, 0), new Point(pictureBox1.Width / 3, pictureBox1.Height));
                g.DrawLine(new Pen(Brushes.Black, 2), new Point(0, pictureBox1.Height / 3), new Point(pictureBox1.Width, pictureBox1.Height / 3));
                g.DrawLine(new Pen(Brushes.Black, 2), new Point(0, (pictureBox1.Height / 3) * 2), new Point(pictureBox1.Width, (pictureBox1.Height / 3) * 2));
                return;
            }

            

            if (radioButton1.Checked == false & radioButton2.Checked == false & radioButton3.Checked == false)
            {
                 button2.Enabled = false;
                radioButton1.Checked = false;
                DialogResult result = MessageBox.Show("Вы не выбрали режим игры, хотите сыграть по моим правилам?", "Режим игры", MessageBoxButtons.YesNo, MessageBoxIcon.Question);
                if (result == DialogResult.Yes)
                {
                    pictureBox1.Image = Properties.Resources._3х3;
                    label2.Text = "Ходят : Крестики";
                    button1.Enabled = false;
                    button2.Enabled = true;
                    checkBox1.Checked = false;
                    radioButton1.Checked = true;
                    radioButton1.Enabled = false;
                    radioButton2.Enabled = false;
                    radioButton3.Enabled = false;
                    checkBox1.Enabled = false;
                    g.DrawLine(new Pen(Brushes.Black, 2), new Point((pictureBox1.Width / 3) * 2, 0), new Point((pictureBox1.Width / 3) * 2, pictureBox1.Height));
                    g.DrawLine(new Pen(Brushes.Black, 2), new Point(pictureBox1.Width / 3, 0), new Point(pictureBox1.Width / 3, pictureBox1.Height));
                    g.DrawLine(new Pen(Brushes.Black, 2), new Point(0, pictureBox1.Height / 3), new Point(pictureBox1.Width, pictureBox1.Height / 3));
                    g.DrawLine(new Pen(Brushes.Black, 2), new Point(0, (pictureBox1.Height / 3) * 2), new Point(pictureBox1.Width, (pictureBox1.Height / 3) * 2));
                    return;
                }
                else
                {
                    MessageBox.Show("Для начала игру нужно выбрать режим", "Режим игры", MessageBoxButtons.OK, MessageBoxIcon.Warning);
                    return;
                }
                
            }
           
           
            
            
        }

        private void pictureBox1_MouseClick(object sender, MouseEventArgs e)
        { Graphics g = pictureBox1.CreateGraphics();
            Pen p = new Pen(Brushes.Black, 2);
            Point q = pictureBox1.PointToClient(System.Windows.Forms.Cursor.Position);
            //    (q.X > pictureBox1.Width / 4) && (q.X < (pictureBox1.Width / 4) * 3)



            string hod = label2.Text;
            switch (hod)
            {
                case "Ходят : Крестики":

                    if (radioButton2.Checked == true & radioButton2.Enabled == false)
                    {
                            if (q.X == pictureBox1.Width / 4)
                                break;
                            if (q.X == pictureBox1.Width / 4 * 2)
                                break;
                            if (q.X == pictureBox1.Width / 4 * 3)
                                break;
                            if (q.Y == pictureBox1.Width / 4)
                                break;
                            if (q.Y == pictureBox1.Width / 4 * 2)
                                break;
                            if (q.Y == pictureBox1.Width / 4 * 3)
                                break;
                        if ((q.X < pictureBox1.Width / 4) && (q.Y < pictureBox1.Width / 4))
                        {
                            
                            if (label3.Text == "1")
                            {
                                g.DrawLine(p, 5, 5, pictureBox1.Width / 4 - 5, pictureBox1.Height / 4 - 5); //верхний левый
                                g.DrawLine(p, 5, pictureBox1.Width / 4 - 5, pictureBox1.Height / 4 - 5, 5);
                                label3.Text = "2";
                            }
                            else
                            {
                                break;
                            }


                        }

                        if ((q.X < pictureBox1.Width / 4) && (q.Y < pictureBox1.Width / 4 * 2) && (q.Y > pictureBox1.Width / 4))
                        {
                            if (label8.Text == "1")
                            {
                                g.DrawLine(p, 5, pictureBox1.Width / 4 * 2 - 5, pictureBox1.Width / 4 - 5, pictureBox1.Height / 4 + 5); //центральный левый
                                g.DrawLine(p, 5, pictureBox1.Width / 4 + 5, pictureBox1.Height / 4 - 5, pictureBox1.Height / 4 * 2 - 5);
                                label8.Text = "2";
                            }
                            else
                            {
                                break;
                            }

                        }

                        if ((q.X < pictureBox1.Width / 4) && (q.Y > pictureBox1.Width / 4 * 2) && (q.Y < pictureBox1.Width / 4 * 3))
                        {
                            if (label13.Text == "1")
                            {
                                g.DrawLine(p, 5, pictureBox1.Width / 4 * 2 + 5, pictureBox1.Width / 4 - 5, pictureBox1.Height / 4 * 3 - 5); //нижний левый
                                g.DrawLine(p, 5, pictureBox1.Width / 4 * 3 - 5, pictureBox1.Height / 4 - 5, pictureBox1.Height / 4 * 2 + 5);
                                label13.Text = "2";
                            }
                            else
                            {
                                break;
                            }

                        }
                        if ((q.X < pictureBox1.Width / 4) && (q.Y > pictureBox1.Width / 4 * 3))
                        {
                            if (label18.Text == "1")
                            {
                                g.DrawLine(p, 5, pictureBox1.Width / 4 * 3 + 6, pictureBox1.Width / 4 - 5, pictureBox1.Height - 6); //нижний левый
                                g.DrawLine(p, 5, pictureBox1.Width - 6, pictureBox1.Height / 4 - 5, pictureBox1.Height / 4 * 3 + 6);
                                label18.Text = "2";
                            }
                            else
                            {
                                break;
                            }

                        }
                        // 2 stolbik
                        if ((q.X > pictureBox1.Width / 4) && (q.X < (pictureBox1.Width / 4) * 2) && (q.Y < pictureBox1.Width / 4))
                        {
                            if (label4.Text == "1")
                            {
                                g.DrawLine(p, pictureBox1.Width / 4 + 5, 5, (pictureBox1.Height / 4) * 2 - 5, pictureBox1.Width / 4 - 5); // верхний центральный
                                g.DrawLine(p, (pictureBox1.Width / 4) * 2 - 5, 5, pictureBox1.Width / 4 + 5, pictureBox1.Height / 4 - 5);
                                label4.Text = "2";
                            }
                            else
                            {
                                break;
                            }

                        }

                        if ((q.X > pictureBox1.Width / 4) && (q.X < (pictureBox1.Width / 4) * 2) && (q.Y < pictureBox1.Width / 4 * 2) && (q.Y > pictureBox1.Width / 4))
                        {
                            if (label9.Text == "1")
                            {
                                g.DrawLine(p, pictureBox1.Width / 4 + 5, (pictureBox1.Height / 4) * 2 - 5, (pictureBox1.Height / 4) * 2 - 5, pictureBox1.Width / 4 + 5); //центральный
                                g.DrawLine(p, (pictureBox1.Width / 4) * 2 - 5, (pictureBox1.Height / 4) * 2 - 5, pictureBox1.Width / 4 + 5, pictureBox1.Height / 4 + 5);
                                label9.Text = "2";
                            }
                            else
                            {
                                break;
                            }

                        }

                        if ((q.X > pictureBox1.Width / 4) && (q.X < (pictureBox1.Width / 4) * 2) && (q.Y > pictureBox1.Width / 4 * 2) && (q.Y < pictureBox1.Width / 4 * 3))
                        {
                            if (label14.Text == "1")
                            {
                                g.DrawLine(p, pictureBox1.Width / 4 * 2 - 5, (pictureBox1.Height / 4) * 2 + 5, pictureBox1.Height / 4 + 5, pictureBox1.Width / 4 * 3 - 5); //нижний центральный
                                g.DrawLine(p, (pictureBox1.Width / 4) * 2 - 5, pictureBox1.Height / 4 * 3 - 5, pictureBox1.Width / 4 + 5, pictureBox1.Height / 4 * 2 + 5);
                                label14.Text = "2";
                            }
                            else
                            {
                                break;
                            }

                        }
                        if ((q.X > pictureBox1.Width / 4) && (q.X < (pictureBox1.Width / 4) * 2) && (q.Y > pictureBox1.Width / 4 * 3))
                        {
                            if (label19.Text == "1")
                            {
                                g.DrawLine(p, pictureBox1.Width / 4 + 5, (pictureBox1.Height / 4) * 3 + 6, (pictureBox1.Height / 4) * 2 - 6, pictureBox1.Width - 7); //центральный
                                g.DrawLine(p, (pictureBox1.Width / 4) + 6, pictureBox1.Height - 7, pictureBox1.Width / 4 * 2 - 6, pictureBox1.Height / 4 * 3 + 7);
                                label19.Text = "2";
                            }
                            else
                            {
                                break;
                            }

                        }
                        // 3 stolbik
                        if ((q.X > (pictureBox1.Width / 4) * 2) && (q.X < (pictureBox1.Width / 4) * 3) && (q.Y < pictureBox1.Width / 4))
                        {
                            if (label5.Text == "1")
                            {
                                g.DrawLine(p, pictureBox1.Width / 4 * 2 + 5, 5, pictureBox1.Height / 4 * 3 - 5, pictureBox1.Width / 4 - 5); // верхний левый
                                g.DrawLine(p, pictureBox1.Width / 4 * 3 - 5, 5, pictureBox1.Width / 4 * 2 + 5, pictureBox1.Height / 4 - 5);
                                label5.Text = "2";
                            }
                            else
                            {
                                break;
                            }

                        }

                        if ((q.X > (pictureBox1.Width / 4) * 2) && (q.X < (pictureBox1.Width / 4) * 3) && (q.Y < pictureBox1.Width / 4 * 2) && (q.Y > pictureBox1.Width / 4))
                        {
                            if (label10.Text == "1")
                            {
                                g.DrawLine(p, pictureBox1.Width / 4 * 2 + 5, pictureBox1.Width / 4 + 5, pictureBox1.Height / 4 * 3 - 5, pictureBox1.Width / 4 * 2 - 5); //центральный левый
                                g.DrawLine(p, pictureBox1.Width / 4 * 3 - 5, pictureBox1.Width / 4 + 5, pictureBox1.Width / 4 * 2 + 5, pictureBox1.Height / 4 * 2 - 5);
                                label10.Text = "2";
                            }
                            else
                            {
                                break;
                            }

                        }

                        if ((q.X > (pictureBox1.Width / 4) * 2) && (q.X < (pictureBox1.Width / 4) * 3) && (q.Y > pictureBox1.Width / 4 * 2) && (q.Y < pictureBox1.Width / 4 * 3))
                        {
                            if (label15.Text == "1")
                            {
                                g.DrawLine(p, pictureBox1.Width / 4 * 2 + 5, pictureBox1.Width / 4 * 2 + 5, pictureBox1.Height / 4 * 3 - 5, pictureBox1.Width / 4 * 3 - 5); //нижний праый
                                g.DrawLine(p, pictureBox1.Width / 4 * 3 - 5, pictureBox1.Width / 4 * 2 + 5, pictureBox1.Width / 4 * 2 + 5, pictureBox1.Height / 4 * 3 - 5);
                                label15.Text = "2";
                            }
                            else
                            {
                                break;
                            }

                        }
                        if ((q.X > (pictureBox1.Width / 4) * 2) && (q.X < (pictureBox1.Width / 4) * 3) && (q.Y > pictureBox1.Width / 4 * 3))
                        {
                            if (label20.Text == "1")
                            {
                                g.DrawLine(p, pictureBox1.Width / 4 * 2 + 5, pictureBox1.Width / 4 * 3 + 6, pictureBox1.Height / 4 * 3 - 5, pictureBox1.Width - 6); //нижний праый
                                g.DrawLine(p, pictureBox1.Width / 4 * 2 + 5, pictureBox1.Width - 6, pictureBox1.Width / 4 * 3 - 5, pictureBox1.Height / 4 * 3 + 6);
                                label20.Text = "2";
                            }
                            else
                            {
                                break;
                            }

                        }
                        //4 stolbik
                        if ((q.X > (pictureBox1.Width / 4) * 3) && (q.Y < pictureBox1.Width / 4))
                        {
                            if (label6.Text == "1")
                            {
                                g.DrawLine(p, pictureBox1.Width / 4 * 3 + 6, 6, pictureBox1.Height - 7, pictureBox1.Width / 4 - 5); // верхний левый
                                g.DrawLine(p, pictureBox1.Width - 6, 6, pictureBox1.Width / 4 * 3 + 7, pictureBox1.Height / 4 - 5);
                                label6.Text = "2";
                            }
                            else
                            {
                                break;
                            }

                        }

                        if ((q.X > (pictureBox1.Width / 4) * 3) && (q.Y < pictureBox1.Width / 4 * 2) && (q.Y > pictureBox1.Width / 4))
                        {
                            if (label11.Text == "1")
                            {
                                g.DrawLine(p, pictureBox1.Width / 4 * 3 + 6, pictureBox1.Width / 4 + 6, pictureBox1.Height - 7, pictureBox1.Width / 4 * 2 - 5); //центральный левый
                                g.DrawLine(p, pictureBox1.Width - 6, pictureBox1.Width / 4 + 6, pictureBox1.Width / 4 * 3 + 7, pictureBox1.Height / 4 * 2 - 5);
                                label11.Text = "2";
                            }
                            else
                            {
                                break;
                            }

                        }

                        if ((q.X > (pictureBox1.Width / 4) * 3) && (q.Y > pictureBox1.Width / 4 * 2) && (q.Y < pictureBox1.Width / 4 * 3))
                        {
                            if (label16.Text == "1")
                            {
                                g.DrawLine(p, pictureBox1.Width / 4 * 3 + 6, pictureBox1.Width / 4 * 2 + 6, pictureBox1.Height - 7, pictureBox1.Width / 4 * 3 - 5); //нижний праый
                                g.DrawLine(p, pictureBox1.Width - 6, pictureBox1.Width / 4 * 2 + 6, pictureBox1.Width / 4 * 3 + 7, pictureBox1.Height / 4 * 3 - 5);
                                label16.Text = "2";
                            }
                            else
                            {
                                break;
                            }

                        }
                        if ((q.X > (pictureBox1.Width / 4) * 3) && (q.Y > pictureBox1.Width / 4 * 3))
                        {
                            if (label21.Text == "1")
                            {
                                g.DrawLine(p, pictureBox1.Width - 6, pictureBox1.Width / 4 * 3 + 5, pictureBox1.Height / 4 * 3 + 5, pictureBox1.Width - 6); //нижний праый
                                g.DrawLine(p, pictureBox1.Width - 5, pictureBox1.Width - 5, pictureBox1.Width / 4 * 3 + 5, pictureBox1.Height / 4 * 3 + 5);
                                label21.Text = "2";
                            }
                            else
                            {
                                break;
                            }

                        }
                        int j3;
                        int j4;
                        int j5;
                        int j6;
                        int j7;
                        int j8;
                        int j9;
                        int j10;
                        int j11;
                        int j12;
                        int j13;
                        int j14;
                        int j15;
                        int j16;
                        int j17;
                        int j18;
                        int j19;
                        int j20;
                        int j21;
                        int j22;
                        int j23;
                        int j24;
                        int j25;
                        int j26;
                        int j27;
                        Int32.TryParse(label3.Text, out j3);
                        Int32.TryParse(label4.Text, out j4);
                        Int32.TryParse(label5.Text, out j5);
                        Int32.TryParse(label6.Text, out j6);
                        Int32.TryParse(label7.Text, out j7);
                        Int32.TryParse(label8.Text, out j8);
                        Int32.TryParse(label9.Text, out j9);
                        Int32.TryParse(label10.Text, out j10);
                        Int32.TryParse(label11.Text, out j11);
                        Int32.TryParse(label12.Text, out j12);
                        Int32.TryParse(label13.Text, out j13);
                        Int32.TryParse(label14.Text, out j14);
                        Int32.TryParse(label15.Text, out j15);
                        Int32.TryParse(label16.Text, out j16);
                        Int32.TryParse(label17.Text, out j17);
                        Int32.TryParse(label18.Text, out j18);
                        Int32.TryParse(label19.Text, out j19);
                        Int32.TryParse(label20.Text, out j20);
                        Int32.TryParse(label21.Text, out j21);
                        Int32.TryParse(label22.Text, out j22);
                        Int32.TryParse(label23.Text, out j23);
                        Int32.TryParse(label24.Text, out j24);
                        Int32.TryParse(label25.Text, out j25);
                        Int32.TryParse(label26.Text, out j26);
                        Int32.TryParse(label27.Text, out j27);
                        if ((j6 == 2) && (j10 == 2) && (j14 == 2) && (j18 == 2))
                        {
                            MessageBox.Show("Победили крестики");
                            
                            DialogResult result = MessageBox.Show("Вы хотите сыграть еще раз", "Новая игра", MessageBoxButtons.YesNo, MessageBoxIcon.Question);
                            if (result == DialogResult.Yes)
                            {
                                pictureBox1.Image = Properties.Resources._2;
                                label2.Text = "Ожидание начала игры";
                                label3.Text = "1";
                                label4.Text = "1";
                                label5.Text = "1";
                                label6.Text = "1";
                                label7.Text = "1";
                                label8.Text = "1";
                                label9.Text = "1";
                                label10.Text = "1";
                                label11.Text = "1";
                                label12.Text = "1";
                                label13.Text = "1";
                                label14.Text = "1";
                                label15.Text = "1";
                                label16.Text = "1";
                                label17.Text = "1";
                                label18.Text = "1";
                                label19.Text = "1";
                                label20.Text = "1";
                                label21.Text = "1";
                                label22.Text = "1";
                                label23.Text = "1";
                                label24.Text = "1";
                                label25.Text = "1";
                                label26.Text = "1";
                                label27.Text = "1";
                                radioButton1.Checked = false;
                                radioButton2.Checked = false;
                                radioButton3.Checked = false;
                                checkBox1.Checked = false;
                                button1.Enabled = true;
                                button2.Enabled = false;
                                radioButton1.Enabled = true;
                                radioButton2.Enabled = true;
                                radioButton3.Enabled = true;
                                checkBox1.Enabled = true;                              
                                break;
                            }
                            else
                                Close();
                        }
                        if ((j3 == 2) && (j9 == 2) && (j15 == 2) && (j21 == 2))
                        {
                            MessageBox.Show("Победили крестики");
                            DialogResult result = MessageBox.Show("Вы хотите сыграть еще раз", "Новая игра", MessageBoxButtons.YesNo, MessageBoxIcon.Question);
                            if (result == DialogResult.Yes)
                            {
                                pictureBox1.Image = Properties.Resources._2;
                                label2.Text = "Ожидание начала игры";
                                label3.Text = "1";
                                label4.Text = "1";
                                label5.Text = "1";
                                label6.Text = "1";
                                label7.Text = "1";
                                label8.Text = "1";
                                label9.Text = "1";
                                label10.Text = "1";
                                label11.Text = "1";
                                label12.Text = "1";
                                label13.Text = "1";
                                label14.Text = "1";
                                label15.Text = "1";
                                label16.Text = "1";
                                label17.Text = "1";
                                label18.Text = "1";
                                label19.Text = "1";
                                label20.Text = "1";
                                label21.Text = "1";
                                label22.Text = "1";
                                label23.Text = "1";
                                label24.Text = "1";
                                label25.Text = "1";
                                label26.Text = "1";
                                label27.Text = "1";
                                radioButton1.Checked = false;
                                radioButton2.Checked = false;
                                radioButton3.Checked = false;
                                checkBox1.Checked = false;
                                button1.Enabled = true;
                                button2.Enabled = false;
                                radioButton1.Enabled = true;
                                radioButton2.Enabled = true;
                                radioButton3.Enabled = true;
                                checkBox1.Enabled = true;
                               
                                break;
                            }
                            else
                                Close();
                        }
                        if ((j6 == 2) && (j11 == 2) && (j16 == 2) && (j21 == 2))
                        {
                            MessageBox.Show("Победили крестики");
                            DialogResult result = MessageBox.Show("Вы хотите сыграть еще раз", "Новая игра", MessageBoxButtons.YesNo, MessageBoxIcon.Question);
                            if (result == DialogResult.Yes)
                            {
                                pictureBox1.Image = Properties.Resources._2;
                                label2.Text = "Ожидание начала игры";
                                label3.Text = "1";
                                label4.Text = "1";
                                label5.Text = "1";
                                label6.Text = "1";
                                label7.Text = "1";
                                label8.Text = "1";
                                label9.Text = "1";
                                label10.Text = "1";
                                label11.Text = "1";
                                label12.Text = "1";
                                label13.Text = "1";
                                label14.Text = "1";
                                label15.Text = "1";
                                label16.Text = "1";
                                label17.Text = "1";
                                label18.Text = "1";
                                label19.Text = "1";
                                label20.Text = "1";
                                label21.Text = "1";
                                label22.Text = "1";
                                label23.Text = "1";
                                label24.Text = "1";
                                label25.Text = "1";
                                label26.Text = "1";
                                label27.Text = "1";
                                radioButton1.Checked = false;
                                radioButton2.Checked = false;
                                radioButton3.Checked = false;
                                checkBox1.Checked = false;
                                button1.Enabled = true;
                                button2.Enabled = false;
                                radioButton1.Enabled = true;
                                radioButton2.Enabled = true;
                                radioButton3.Enabled = true;
                                checkBox1.Enabled = true;
                               
                                break;
                            }
                            else
                                Close();
                        }
                        if ((j5 == 2) && (j10 == 2) && (j15 == 2) && (j20 == 2))
                        {
                            MessageBox.Show("Победили крестики");
                            DialogResult result = MessageBox.Show("Вы хотите сыграть еще раз", "Новая игра", MessageBoxButtons.YesNo, MessageBoxIcon.Question);
                            if (result == DialogResult.Yes)
                            {
                                pictureBox1.Image = Properties.Resources._2;
                                label2.Text = "Ожидание начала игры";
                                label3.Text = "1";
                                label4.Text = "1";
                                label5.Text = "1";
                                label6.Text = "1";
                                label7.Text = "1";
                                label8.Text = "1";
                                label9.Text = "1";
                                label10.Text = "1";
                                label11.Text = "1";
                                label12.Text = "1";
                                label13.Text = "1";
                                label14.Text = "1";
                                label15.Text = "1";
                                label16.Text = "1";
                                label17.Text = "1";
                                label18.Text = "1";
                                label19.Text = "1";
                                label20.Text = "1";
                                label21.Text = "1";
                                label22.Text = "1";
                                label23.Text = "1";
                                label24.Text = "1";
                                label25.Text = "1";
                                label26.Text = "1";
                                label27.Text = "1";
                                radioButton1.Checked = false;
                                radioButton2.Checked = false;
                                radioButton3.Checked = false;
                                checkBox1.Checked = false;
                                button1.Enabled = true;
                                button2.Enabled = false;
                                radioButton1.Enabled = true;
                                radioButton2.Enabled = true;
                                radioButton3.Enabled = true;
                                checkBox1.Enabled = true;
                               
                                break;
                            }
                            else
                                Close();
                        }
                        if ((j4 == 2) && (j9 == 2) && (j14 == 2) && (j19 == 2))
                        {
                            MessageBox.Show("Победили крестики");
                            DialogResult result = MessageBox.Show("Вы хотите сыграть еще раз", "Новая игра", MessageBoxButtons.YesNo, MessageBoxIcon.Question);
                            if (result == DialogResult.Yes)
                            {
                                pictureBox1.Image = Properties.Resources._2;
                                label2.Text = "Ожидание начала игры";
                                label3.Text = "1";
                                label4.Text = "1";
                                label5.Text = "1";
                                label6.Text = "1";
                                label7.Text = "1";
                                label8.Text = "1";
                                label9.Text = "1";
                                label10.Text = "1";
                                label11.Text = "1";
                                label12.Text = "1";
                                label13.Text = "1";
                                label14.Text = "1";
                                label15.Text = "1";
                                label16.Text = "1";
                                label17.Text = "1";
                                label18.Text = "1";
                                label19.Text = "1";
                                label20.Text = "1";
                                label21.Text = "1";
                                label22.Text = "1";
                                label23.Text = "1";
                                label24.Text = "1";
                                label25.Text = "1";
                                label26.Text = "1";
                                label27.Text = "1";
                                radioButton1.Checked = false;
                                radioButton2.Checked = false;
                                radioButton3.Checked = false;
                                checkBox1.Checked = false;
                                button1.Enabled = true;
                                button2.Enabled = false;
                                radioButton1.Enabled = true;
                                radioButton2.Enabled = true;
                                radioButton3.Enabled = true;
                                checkBox1.Enabled = true;
                               
                                break;
                            }
                            else
                                Close();
                        }
                        if ((j3 == 2) && (j8 == 2) && (j13 == 2) && (j18 == 2))
                        {
                            MessageBox.Show("Победили крестики");
                            DialogResult result = MessageBox.Show("Вы хотите сыграть еще раз", "Новая игра", MessageBoxButtons.YesNo, MessageBoxIcon.Question);
                            if (result == DialogResult.Yes)
                            {
                                pictureBox1.Image = Properties.Resources._2;
                                label2.Text = "Ожидание начала игры";
                                label3.Text = "1";
                                label4.Text = "1";
                                label5.Text = "1";
                                label6.Text = "1";
                                label7.Text = "1";
                                label8.Text = "1";
                                label9.Text = "1";
                                label10.Text = "1";
                                label11.Text = "1";
                                label12.Text = "1";
                                label13.Text = "1";
                                label14.Text = "1";
                                label15.Text = "1";
                                label16.Text = "1";
                                label17.Text = "1";
                                label18.Text = "1";
                                label19.Text = "1";
                                label20.Text = "1";
                                label21.Text = "1";
                                label22.Text = "1";
                                label23.Text = "1";
                                label24.Text = "1";
                                label25.Text = "1";
                                label26.Text = "1";
                                label27.Text = "1";
                                radioButton1.Checked = false;
                                radioButton2.Checked = false;
                                radioButton3.Checked = false;
                                checkBox1.Checked = false;
                                button1.Enabled = true;
                                button2.Enabled = false;
                                radioButton1.Enabled = true;
                                radioButton2.Enabled = true;
                                radioButton3.Enabled = true;
                                checkBox1.Enabled = true;
                               
                                break;
                            }
                            else
                                Close();
                        }
                        if ((j18 == 2) && (j19 == 2) && (j20 == 2) && (j21 == 2))
                        {
                            MessageBox.Show("Победили крестики");
                            DialogResult result = MessageBox.Show("Вы хотите сыграть еще раз", "Новая игра", MessageBoxButtons.YesNo, MessageBoxIcon.Question);
                            if (result == DialogResult.Yes)
                            {
                                pictureBox1.Image = Properties.Resources._2;
                                label2.Text = "Ожидание начала игры";
                                label3.Text = "1";
                                label4.Text = "1";
                                label5.Text = "1";
                                label6.Text = "1";
                                label7.Text = "1";
                                label8.Text = "1";
                                label9.Text = "1";
                                label10.Text = "1";
                                label11.Text = "1";
                                label12.Text = "1";
                                label13.Text = "1";
                                label14.Text = "1";
                                label15.Text = "1";
                                label16.Text = "1";
                                label17.Text = "1";
                                label18.Text = "1";
                                label19.Text = "1";
                                label20.Text = "1";
                                label21.Text = "1";
                                label22.Text = "1";
                                label23.Text = "1";
                                label24.Text = "1";
                                label25.Text = "1";
                                label26.Text = "1";
                                label27.Text = "1";
                                radioButton1.Checked = false;
                                radioButton2.Checked = false;
                                radioButton3.Checked = false;
                                checkBox1.Checked = false;
                                button1.Enabled = true;
                                button2.Enabled = false;
                                radioButton1.Enabled = true;
                                radioButton2.Enabled = true;
                                radioButton3.Enabled = true;
                                checkBox1.Enabled = true;
                              
                                break;
                            }
                            else
                                Close();
                        }
                        if ((j13 == 2) && (j14 == 2) && (j15 == 2) && (j16 == 2))
                        {
                            MessageBox.Show("Победили крестики");
                            DialogResult result = MessageBox.Show("Вы хотите сыграть еще раз", "Новая игра", MessageBoxButtons.YesNo, MessageBoxIcon.Question);
                            if (result == DialogResult.Yes)
                            {
                                pictureBox1.Image = Properties.Resources._2;
                                label2.Text = "Ожидание начала игры";
                                label3.Text = "1";
                                label4.Text = "1";
                                label5.Text = "1";
                                label6.Text = "1";
                                label7.Text = "1";
                                label8.Text = "1";
                                label9.Text = "1";
                                label10.Text = "1";
                                label11.Text = "1";
                                label12.Text = "1";
                                label13.Text = "1";
                                label14.Text = "1";
                                label15.Text = "1";
                                label16.Text = "1";
                                label17.Text = "1";
                                label18.Text = "1";
                                label19.Text = "1";
                                label20.Text = "1";
                                label21.Text = "1";
                                label22.Text = "1";
                                label23.Text = "1";
                                label24.Text = "1";
                                label25.Text = "1";
                                label26.Text = "1";
                                label27.Text = "1";
                                radioButton1.Checked = false;
                                radioButton2.Checked = false;
                                radioButton3.Checked = false;
                                checkBox1.Checked = false;
                                button1.Enabled = true;
                                button2.Enabled = false;
                                radioButton1.Enabled = true;
                                radioButton2.Enabled = true;
                                radioButton3.Enabled = true;
                                checkBox1.Enabled = true;
                               
                                break;
                            }
                            else
                                Close();
                        }
                        if ((j8 == 2) && (j9 == 2) && (j10 == 2) && (j11 == 2))
                        {
                            MessageBox.Show("Победили крестики");
                            DialogResult result = MessageBox.Show("Вы хотите сыграть еще раз", "Новая игра", MessageBoxButtons.YesNo, MessageBoxIcon.Question);
                            if (result == DialogResult.Yes)
                            {
                                pictureBox1.Image = Properties.Resources._2;
                                label2.Text = "Ожидание начала игры";
                                label3.Text = "1";
                                label4.Text = "1";
                                label5.Text = "1";
                                label6.Text = "1";
                                label7.Text = "1";
                                label8.Text = "1";
                                label9.Text = "1";
                                label10.Text = "1";
                                label11.Text = "1";
                                label12.Text = "1";
                                label13.Text = "1";
                                label14.Text = "1";
                                label15.Text = "1";
                                label16.Text = "1";
                                label17.Text = "1";
                                label18.Text = "1";
                                label19.Text = "1";
                                label20.Text = "1";
                                label21.Text = "1";
                                label22.Text = "1";
                                label23.Text = "1";
                                label24.Text = "1";
                                label25.Text = "1";
                                label26.Text = "1";
                                label27.Text = "1";
                                radioButton1.Checked = false;
                                radioButton2.Checked = false;
                                radioButton3.Checked = false;
                                checkBox1.Checked = false;
                                button1.Enabled = true;
                                button2.Enabled = false;
                                radioButton1.Enabled = true;
                                radioButton2.Enabled = true;
                                radioButton3.Enabled = true;
                                checkBox1.Enabled = true;
                               
                                break;
                            }
                            else
                                Close();
                        }
                        if ((j3 == 2) && (j4 == 2) && (j5 == 2) && (j6 == 2))
                        {
                            MessageBox.Show("Победили крестики");
                            DialogResult result = MessageBox.Show("Вы хотите сыграть еще раз", "Новая игра", MessageBoxButtons.YesNo, MessageBoxIcon.Question);
                            if (result == DialogResult.Yes)
                            {
                                pictureBox1.Image = Properties.Resources._2;
                                label2.Text = "Ожидание начала игры";
                                label3.Text = "1";
                                label4.Text = "1";
                                label5.Text = "1";
                                label6.Text = "1";
                                label7.Text = "1";
                                label8.Text = "1";
                                label9.Text = "1";
                                label10.Text = "1";
                                label11.Text = "1";
                                label12.Text = "1";
                                label13.Text = "1";
                                label14.Text = "1";
                                label15.Text = "1";
                                label16.Text = "1";
                                label17.Text = "1";
                                label18.Text = "1";
                                label19.Text = "1";
                                label20.Text = "1";
                                label21.Text = "1";
                                label22.Text = "1";
                                label23.Text = "1";
                                label24.Text = "1";
                                label25.Text = "1";
                                label26.Text = "1";
                                label27.Text = "1";
                                radioButton1.Checked = false;
                                radioButton2.Checked = false;
                                radioButton3.Checked = false;
                                checkBox1.Checked = false;
                                button1.Enabled = true;
                                button2.Enabled = false;
                                radioButton1.Enabled = true;
                                radioButton2.Enabled = true;
                                radioButton3.Enabled = true;
                                checkBox1.Enabled = true;
                          
                                break;
                            }
                            else
                                Close();
                        }
                        if (j3 != 1 && j4 != 1 && j5 != 1 && j8 != 1 && j9 != 1 && j10 != 1 && j13 != 1 && j14 != 1 && j15 != 1 && j6 != 1 && j11 != 1 && j16 != 1 && j21 != 1 && j18 != 1 && j19 != 1 && j20 != 1)
                        {
                            MessageBox.Show("Ничья");
                            DialogResult result = MessageBox.Show("Вы хотите сыграть еще раз", "Новая игра", MessageBoxButtons.YesNo, MessageBoxIcon.Question);
                            if (result == DialogResult.Yes)
                            {
                                pictureBox1.Image = Properties.Resources._2;
                                label2.Text = "Ожидание начала игры";
                                label3.Text = "1";
                                label4.Text = "1";
                                label5.Text = "1";
                                label6.Text = "1";
                                label7.Text = "1";
                                label8.Text = "1";
                                label9.Text = "1";
                                label10.Text = "1";
                                label11.Text = "1";
                                label12.Text = "1";
                                label13.Text = "1";
                                label14.Text = "1";
                                label15.Text = "1";
                                label16.Text = "1";
                                label17.Text = "1";
                                label18.Text = "1";
                                label19.Text = "1";
                                label20.Text = "1";
                                label21.Text = "1";
                                label22.Text = "1";
                                label23.Text = "1";
                                label24.Text = "1";
                                label25.Text = "1";
                                label26.Text = "1";
                                label27.Text = "1";
                                radioButton1.Checked = false;
                                radioButton2.Checked = false;
                                radioButton3.Checked = false;
                                checkBox1.Checked = false;
                                button1.Enabled = true;
                                button2.Enabled = false;
                                radioButton1.Enabled = true;
                                radioButton2.Enabled = true;
                                radioButton3.Enabled = true;
                                checkBox1.Enabled = true;
                           
                                break;
                            }
                            else
                                Close();
                        }
                    }
                    //3х3
                    if (radioButton1.Checked == true & radioButton1.Enabled == false)
                    {
                        if (q.X == pictureBox1.Width / 3)
                            break;
                        if (q.X == pictureBox1.Width / 3 * 2)
                            break;
                        if (q.Y == pictureBox1.Width / 3)
                            break;
                        if (q.Y == pictureBox1.Width / 3 * 2)
                            break;
                        if ((q.X < pictureBox1.Width / 3) && (q.Y < pictureBox1.Width / 3))
                        {
                            if (label3.Text == "1")
                            {
                                g.DrawLine(p, 5, 5, pictureBox1.Width / 3 - 5, pictureBox1.Height / 3 - 5); //верхний левый
                                g.DrawLine(p, 5, pictureBox1.Width / 3 - 5, pictureBox1.Height / 3 - 5, 5);
                                label3.Text = "2";
                                
                            }
                            else
                            {
                                break;
                            }

                        }

                        if ((q.X < pictureBox1.Width / 3) && (q.Y < pictureBox1.Width / 3 * 2) && (q.Y > pictureBox1.Width / 3))
                        {
                            if (label8.Text == "1")
                            {
                                g.DrawLine(p, 5, pictureBox1.Width / 3 * 2 - 5, pictureBox1.Width / 3 - 5, pictureBox1.Height / 3 + 5); //центральный левый
                                g.DrawLine(p, 5, pictureBox1.Width / 3 + 5, pictureBox1.Height / 3 - 5, pictureBox1.Height / 3 * 2 - 5);                              
                                label8.Text = "2";
                                
                            }
                            else
                            {
                                break;
                            }

                        }

                        if ((q.X < pictureBox1.Width / 3) && (q.Y > pictureBox1.Width / 3 * 2))
                        {
                            if (label13.Text == "1")
                            {
                                g.DrawLine(p, 5, pictureBox1.Width / 3 * 2 + 5, pictureBox1.Width / 3 - 5, pictureBox1.Height - 5); //нижний левый
                                g.DrawLine(p, 5, pictureBox1.Width - 5, pictureBox1.Height / 3 - 5, pictureBox1.Height / 3 * 2 + 5);
                                label13.Text = "2";
                               
                            }
                            else
                            {
                                break;
                            }

                        }
                        // 2 столбик
                        if ((q.X < (pictureBox1.Width / 3) * 2) && (q.X > pictureBox1.Width / 3) && (q.Y < pictureBox1.Width / 3))
                        {
                            if (label4.Text == "1")
                            {
                                g.DrawLine(p, pictureBox1.Width / 3 + 5, 5, (pictureBox1.Height / 3) * 2 - 5, pictureBox1.Width / 3 - 5); // верхний центральный
                                g.DrawLine(p, (pictureBox1.Width / 3) * 2 - 5, 5, pictureBox1.Width / 3 + 5, pictureBox1.Height / 3 - 5);
                                label4.Text = "2";
                                
                            }
                            else
                            {
                                break;
                            }

                        }

                        if ((q.X < (pictureBox1.Width / 3) * 2) && (q.X > pictureBox1.Width / 3) && (q.Y < pictureBox1.Width / 3 * 2) && (q.Y > pictureBox1.Width / 3))
                        {
                            if (label9.Text == "1")
                            {
                                g.DrawLine(p, pictureBox1.Width / 3 + 5, (pictureBox1.Height / 3) * 2 - 5, (pictureBox1.Height / 3) * 2 - 5, pictureBox1.Width / 3 + 5); //центральный
                                g.DrawLine(p, (pictureBox1.Width / 3) * 2 - 5, (pictureBox1.Height / 3) * 2 - 5, pictureBox1.Width / 3 + 5, pictureBox1.Height / 3 + 5);
                                label9.Text = "2";
                            }
                            else
                            {
                                break;
                            }

                        }

                        if ((q.X < (pictureBox1.Width / 3) * 2) && (q.X > pictureBox1.Width / 3) && (q.Y > pictureBox1.Width / 3 * 2))
                        {
                            if (label14.Text == "1")
                            {
                                g.DrawLine(p, pictureBox1.Width / 3 * 2 - 5, (pictureBox1.Height / 3) * 2 + 5, pictureBox1.Height / 3 + 5, pictureBox1.Width - 5); //нижний центральный
                                g.DrawLine(p, (pictureBox1.Width / 3) * 2 - 5, pictureBox1.Height - 5, pictureBox1.Width / 3 + 5, pictureBox1.Height / 3 * 2 + 5);
                                label14.Text = "2";
                            }
                            else
                            {
                                break;
                            }

                        }
                        // 3 столбик
                        if ((q.X > (pictureBox1.Width / 3) * 2) && (q.Y < pictureBox1.Width / 3))
                        {
                            if (label5.Text == "1")
                            {
                                g.DrawLine(p, pictureBox1.Width / 3 * 2 + 5, 5, pictureBox1.Height - 5, pictureBox1.Width / 3 - 5); // верхний левый
                                g.DrawLine(p, pictureBox1.Width - 5, 5, pictureBox1.Width / 3 * 2 + 5, pictureBox1.Height / 3 - 5);
                                label5.Text = "2";
                            }
                            else
                            {
                                break;
                            }

                        }

                        if ((q.X > (pictureBox1.Width / 3) * 2) && (q.Y < pictureBox1.Width / 3 * 2) && (q.Y > pictureBox1.Width / 3))
                        {
                            if (label10.Text == "1")
                            {
                                g.DrawLine(p, pictureBox1.Width / 3 * 2 + 5, pictureBox1.Width / 3 + 5, pictureBox1.Height - 5, pictureBox1.Width / 3 * 2 - 5); //центральный левый
                                g.DrawLine(p, pictureBox1.Width - 5, pictureBox1.Width / 3 + 5, pictureBox1.Width / 3 * 2 + 5, pictureBox1.Height / 3 * 2 - 5);
                                label10.Text = "2";
                            }
                            else
                            {
                                break;
                            }

                        }

                        if ((q.X > (pictureBox1.Width / 3) * 2) && (q.Y > pictureBox1.Width / 3 * 2))
                        {
                            if (label15.Text == "1")
                            {
                                g.DrawLine(p, pictureBox1.Width / 3 * 2 + 5, pictureBox1.Width / 3 * 2 + 5, pictureBox1.Height - 5, pictureBox1.Width - 5); //нижний праый
                                g.DrawLine(p, pictureBox1.Width - 5, pictureBox1.Width / 3 * 2 + 5, pictureBox1.Width / 3 * 2 + 5, pictureBox1.Height - 5);
                                label15.Text = "2";
                            }
                            else
                            {
                                break;
                            }

                        }
                        int j3;
                        int j4;
                        int j5;
                        int j6;
                        int j7;
                        int j8;
                        int j9;
                        int j10;
                        int j11;
                        int j12;
                        int j13;
                        int j14;
                        int j15;
                        int j16;
                        int j17;
                        int j18;
                        int j19;
                        int j20;
                        int j21;
                        int j22;
                        int j23;
                        int j24;
                        int j25;
                        int j26;
                        int j27;
                        Int32.TryParse(label3.Text, out j3);
                        Int32.TryParse(label4.Text, out j4);
                        Int32.TryParse(label5.Text, out j5);
                        Int32.TryParse(label6.Text, out j6);
                        Int32.TryParse(label7.Text, out j7);
                        Int32.TryParse(label8.Text, out j8);
                        Int32.TryParse(label9.Text, out j9);
                        Int32.TryParse(label10.Text, out j10);
                        Int32.TryParse(label11.Text, out j11);
                        Int32.TryParse(label12.Text, out j12);
                        Int32.TryParse(label13.Text, out j13);
                        Int32.TryParse(label14.Text, out j14);
                        Int32.TryParse(label15.Text, out j15);
                        Int32.TryParse(label16.Text, out j16);
                        Int32.TryParse(label17.Text, out j17);
                        Int32.TryParse(label18.Text, out j18);
                        Int32.TryParse(label19.Text, out j19);
                        Int32.TryParse(label20.Text, out j20);
                        Int32.TryParse(label21.Text, out j21);
                        Int32.TryParse(label22.Text, out j22);
                        Int32.TryParse(label23.Text, out j23);
                        Int32.TryParse(label24.Text, out j24);
                        Int32.TryParse(label25.Text, out j25);
                        Int32.TryParse(label26.Text, out j26);
                        Int32.TryParse(label27.Text, out j27);
                        if ((j5 == 2) && (j9 == 2) && (j13 == 2))
                        {
                            MessageBox.Show("Победили крестики");
                            DialogResult result = MessageBox.Show("Вы хотите сыграть еще раз", "Новая игра", MessageBoxButtons.YesNo, MessageBoxIcon.Question);
                            if (result == DialogResult.Yes)
                            {
                                pictureBox1.Image = Properties.Resources._2;
                                label2.Text = "Ожидание начала игры";
                                label3.Text = "1";
                                label4.Text = "1";
                                label5.Text = "1";
                                label6.Text = "1";
                                label7.Text = "1";
                                label8.Text = "1";
                                label9.Text = "1";
                                label10.Text = "1";
                                label11.Text = "1";
                                label12.Text = "1";
                                label13.Text = "1";
                                label14.Text = "1";
                                label15.Text = "1";
                                label16.Text = "1";
                                label17.Text = "1";
                                label18.Text = "1";
                                label19.Text = "1";
                                label20.Text = "1";
                                label21.Text = "1";
                                label22.Text = "1";
                                label23.Text = "1";
                                label24.Text = "1";
                                label25.Text = "1";
                                label26.Text = "1";
                                label27.Text = "1";
                                radioButton1.Checked = false;
                                radioButton2.Checked = false;
                                radioButton3.Checked = false;
                                checkBox1.Checked = false;
                                button1.Enabled = true;
                                button2.Enabled = false;
                                radioButton1.Enabled = true;
                                radioButton2.Enabled = true;
                                radioButton3.Enabled = true;
                                checkBox1.Enabled = true;
                               
                                break;
                            }
                            else
                                Close();
                        }
                        if ((j3 == 2) && (j9 == 2) && (j15 == 2))
                        {
                            MessageBox.Show("Победили крестики");
                            DialogResult result = MessageBox.Show("Вы хотите сыграть еще раз", "Новая игра", MessageBoxButtons.YesNo, MessageBoxIcon.Question);
                            if (result == DialogResult.Yes)
                            {
                                pictureBox1.Image = Properties.Resources._2;
                                label2.Text = "Ожидание начала игры";
                                label3.Text = "1";
                                label4.Text = "1";
                                label5.Text = "1";
                                label6.Text = "1";
                                label7.Text = "1";
                                label8.Text = "1";
                                label9.Text = "1";
                                label10.Text = "1";
                                label11.Text = "1";
                                label12.Text = "1";
                                label13.Text = "1";
                                label14.Text = "1";
                                label15.Text = "1";
                                label16.Text = "1";
                                label17.Text = "1";
                                label18.Text = "1";
                                label19.Text = "1";
                                label20.Text = "1";
                                label21.Text = "1";
                                label22.Text = "1";
                                label23.Text = "1";
                                label24.Text = "1";
                                label25.Text = "1";
                                label26.Text = "1";
                                label27.Text = "1";
                                radioButton1.Checked = false;
                                radioButton2.Checked = false;
                                radioButton3.Checked = false;
                                checkBox1.Checked = false;
                                button1.Enabled = true;
                                button2.Enabled = false;
                                radioButton1.Enabled = true;
                                radioButton2.Enabled = true;
                                radioButton3.Enabled = true;
                                checkBox1.Enabled = true;
                           
                                break;
                            }
                            else
                                Close();
                        }
                        if ((j5 == 2) && (j10 == 2) && (j15 == 2))
                        {
                            MessageBox.Show("Победили крестики");
                            DialogResult result = MessageBox.Show("Вы хотите сыграть еще раз", "Новая игра", MessageBoxButtons.YesNo, MessageBoxIcon.Question);
                            if (result == DialogResult.Yes)
                            {
                                pictureBox1.Image = Properties.Resources._2;
                                label2.Text = "Ожидание начала игры";
                                label3.Text = "1";
                                label4.Text = "1";
                                label5.Text = "1";
                                label6.Text = "1";
                                label7.Text = "1";
                                label8.Text = "1";
                                label9.Text = "1";
                                label10.Text = "1";
                                label11.Text = "1";
                                label12.Text = "1";
                                label13.Text = "1";
                                label14.Text = "1";
                                label15.Text = "1";
                                label16.Text = "1";
                                label17.Text = "1";
                                label18.Text = "1";
                                label19.Text = "1";
                                label20.Text = "1";
                                label21.Text = "1";
                                label22.Text = "1";
                                label23.Text = "1";
                                label24.Text = "1";
                                label25.Text = "1";
                                label26.Text = "1";
                                label27.Text = "1";
                                radioButton1.Checked = false;
                                radioButton2.Checked = false;
                                radioButton3.Checked = false;
                                checkBox1.Checked = false;
                                button1.Enabled = true;
                                button2.Enabled = false;
                                radioButton1.Enabled = true;
                                radioButton2.Enabled = true;
                                radioButton3.Enabled = true;
                                checkBox1.Enabled = true;
                            
                                break;
                            }
                            else
                                Close();
                        }
                        if ((j4 == 2) && (j9 == 2) && (j14 == 2))
                        {
                            MessageBox.Show("Победили крестики");
                            DialogResult result = MessageBox.Show("Вы хотите сыграть еще раз", "Новая игра", MessageBoxButtons.YesNo, MessageBoxIcon.Question);
                            if (result == DialogResult.Yes)
                            {
                                pictureBox1.Image = Properties.Resources._2;
                                label2.Text = "Ожидание начала игры";
                                label3.Text = "1";
                                label4.Text = "1";
                                label5.Text = "1";
                                label6.Text = "1";
                                label7.Text = "1";
                                label8.Text = "1";
                                label9.Text = "1";
                                label10.Text = "1";
                                label11.Text = "1";
                                label12.Text = "1";
                                label13.Text = "1";
                                label14.Text = "1";
                                label15.Text = "1";
                                label16.Text = "1";
                                label17.Text = "1";
                                label18.Text = "1";
                                label19.Text = "1";
                                label20.Text = "1";
                                label21.Text = "1";
                                label22.Text = "1";
                                label23.Text = "1";
                                label24.Text = "1";
                                label25.Text = "1";
                                label26.Text = "1";
                                label27.Text = "1";
                                radioButton1.Checked = false;
                                radioButton2.Checked = false;
                                radioButton3.Checked = false;
                                checkBox1.Checked = false;
                                button1.Enabled = true;
                                button2.Enabled = false;
                                radioButton1.Enabled = true;
                                radioButton2.Enabled = true;
                                radioButton3.Enabled = true;
                                checkBox1.Enabled = true;
                        
                                break;
                            }
                            else
                                Close();
                        }
                        if ((j3 == 2) && (j8 == 2) && (j13 == 2))
                        {
                            MessageBox.Show("Победили крестики");
                            DialogResult result = MessageBox.Show("Вы хотите сыграть еще раз", "Новая игра", MessageBoxButtons.YesNo, MessageBoxIcon.Question);
                            if (result == DialogResult.Yes)
                            {
                                pictureBox1.Image = Properties.Resources._2;
                                label2.Text = "Ожидание начала игры";
                                label3.Text = "1";
                                label4.Text = "1";
                                label5.Text = "1";
                                label6.Text = "1";
                                label7.Text = "1";
                                label8.Text = "1";
                                label9.Text = "1";
                                label10.Text = "1";
                                label11.Text = "1";
                                label12.Text = "1";
                                label13.Text = "1";
                                label14.Text = "1";
                                label15.Text = "1";
                                label16.Text = "1";
                                label17.Text = "1";
                                label18.Text = "1";
                                label19.Text = "1";
                                label20.Text = "1";
                                label21.Text = "1";
                                label22.Text = "1";
                                label23.Text = "1";
                                label24.Text = "1";
                                label25.Text = "1";
                                label26.Text = "1";
                                label27.Text = "1";
                                radioButton1.Checked = false;
                                radioButton2.Checked = false;
                                radioButton3.Checked = false;
                                checkBox1.Checked = false;
                                button1.Enabled = true;
                                button2.Enabled = false;
                                radioButton1.Enabled = true;
                                radioButton2.Enabled = true;
                                radioButton3.Enabled = true;
                                checkBox1.Enabled = true;
                       
                                break;
                            }
                            else
                                Close();
                        }
                        if ((j13 == 2) && (j14 == 2) && (j15 == 2))
                        {
                            MessageBox.Show("Победили крестики");
                            DialogResult result = MessageBox.Show("Вы хотите сыграть еще раз", "Новая игра", MessageBoxButtons.YesNo, MessageBoxIcon.Question);
                            if (result == DialogResult.Yes)
                            {
                                pictureBox1.Image = Properties.Resources._2;
                                label2.Text = "Ожидание начала игры";
                                label3.Text = "1";
                                label4.Text = "1";
                                label5.Text = "1";
                                label6.Text = "1";
                                label7.Text = "1";
                                label8.Text = "1";
                                label9.Text = "1";
                                label10.Text = "1";
                                label11.Text = "1";
                                label12.Text = "1";
                                label13.Text = "1";
                                label14.Text = "1";
                                label15.Text = "1";
                                label16.Text = "1";
                                label17.Text = "1";
                                label18.Text = "1";
                                label19.Text = "1";
                                label20.Text = "1";
                                label21.Text = "1";
                                label22.Text = "1";
                                label23.Text = "1";
                                label24.Text = "1";
                                label25.Text = "1";
                                label26.Text = "1";
                                label27.Text = "1";
                                radioButton1.Checked = false;
                                radioButton2.Checked = false;
                                radioButton3.Checked = false;
                                checkBox1.Checked = false;
                                button1.Enabled = true;
                                button2.Enabled = false;
                                radioButton1.Enabled = true;
                                radioButton2.Enabled = true;
                                radioButton3.Enabled = true;
                                checkBox1.Enabled = true;
                            
                                break;
                            }
                            else
                                Close();
                        }
                        if ((j8 == 2) && (j9 == 2) && (j10 == 2))
                        {
                            MessageBox.Show("Победили крестики");
                            DialogResult result = MessageBox.Show("Вы хотите сыграть еще раз", "Новая игра", MessageBoxButtons.YesNo, MessageBoxIcon.Question);
                            if (result == DialogResult.Yes)
                            {
                                pictureBox1.Image = Properties.Resources._2;
                                label2.Text = "Ожидание начала игры";
                                label3.Text = "1";
                                label4.Text = "1";
                                label5.Text = "1";
                                label6.Text = "1";
                                label7.Text = "1";
                                label8.Text = "1";
                                label9.Text = "1";
                                label10.Text = "1";
                                label11.Text = "1";
                                label12.Text = "1";
                                label13.Text = "1";
                                label14.Text = "1";
                                label15.Text = "1";
                                label16.Text = "1";
                                label17.Text = "1";
                                label18.Text = "1";
                                label19.Text = "1";
                                label20.Text = "1";
                                label21.Text = "1";
                                label22.Text = "1";
                                label23.Text = "1";
                                label24.Text = "1";
                                label25.Text = "1";
                                label26.Text = "1";
                                label27.Text = "1";
                                radioButton1.Checked = false;
                                radioButton2.Checked = false;
                                radioButton3.Checked = false;
                                checkBox1.Checked = false;
                                button1.Enabled = true;
                                button2.Enabled = false;
                                radioButton1.Enabled = true;
                                radioButton2.Enabled = true;
                                radioButton3.Enabled = true;
                                checkBox1.Enabled = true;
                               
                                break;
                            }
                            else
                                Close();
                        }
                        if ((j3 == 2) && (j4 == 2) && (j5 == 2))
                        {
                            MessageBox.Show("Победили крестики");
                            DialogResult result = MessageBox.Show("Вы хотите сыграть еще раз", "Новая игра", MessageBoxButtons.YesNo, MessageBoxIcon.Question);
                            if (result == DialogResult.Yes)
                            {
                                pictureBox1.Image = Properties.Resources._2;
                                label2.Text = "Ожидание начала игры";
                                label3.Text = "1";
                                label4.Text = "1";
                                label5.Text = "1";
                                label6.Text = "1";
                                label7.Text = "1";
                                label8.Text = "1";
                                label9.Text = "1";
                                label10.Text = "1";
                                label11.Text = "1";
                                label12.Text = "1";
                                label13.Text = "1";
                                label14.Text = "1";
                                label15.Text = "1";
                                label16.Text = "1";
                                label17.Text = "1";
                                label18.Text = "1";
                                label19.Text = "1";
                                label20.Text = "1";
                                label21.Text = "1";
                                label22.Text = "1";
                                label23.Text = "1";
                                label24.Text = "1";
                                label25.Text = "1";
                                label26.Text = "1";
                                label27.Text = "1";
                                radioButton1.Checked = false;
                                radioButton2.Checked = false;
                                radioButton3.Checked = false;
                                checkBox1.Checked = false;
                                button1.Enabled = true;
                                button2.Enabled = false;
                                radioButton1.Enabled = true;
                                radioButton2.Enabled = true;
                                radioButton3.Enabled = true;
                                checkBox1.Enabled = true;
                           
                                break;
                            }
                            else
                                Close();
                        }
                        if (j3 != 1 && j4 != 1 && j5 != 1 && j8 != 1 && j9 != 1 && j10 != 1 && j13 != 1 && j14 != 1 && j15 != 1)
                        {
                            MessageBox.Show("Ничья");
                            DialogResult result = MessageBox.Show("Вы хотите сыграть еще раз", "Новая игра", MessageBoxButtons.YesNo, MessageBoxIcon.Question);
                            if (result == DialogResult.Yes)
                            {
                                pictureBox1.Image = Properties.Resources._2;
                                label2.Text = "Ожидание начала игры";
                                label3.Text = "1";
                                label4.Text = "1";
                                label5.Text = "1";
                                label6.Text = "1";
                                label7.Text = "1";
                                label8.Text = "1";
                                label9.Text = "1";
                                label10.Text = "1";
                                label11.Text = "1";
                                label12.Text = "1";
                                label13.Text = "1";
                                label14.Text = "1";
                                label15.Text = "1";
                                label16.Text = "1";
                                label17.Text = "1";
                                label18.Text = "1";
                                label19.Text = "1";
                                label20.Text = "1";
                                label21.Text = "1";
                                label22.Text = "1";
                                label23.Text = "1";
                                label24.Text = "1";
                                label25.Text = "1";
                                label26.Text = "1";
                                label27.Text = "1";
                                radioButton1.Checked = false;
                                radioButton2.Checked = false;
                                radioButton3.Checked = false;
                                checkBox1.Checked = false;
                                button1.Enabled = true;
                                button2.Enabled = false;
                                radioButton1.Enabled = true;
                                radioButton2.Enabled = true;
                                radioButton3.Enabled = true;
                                checkBox1.Enabled = true;
                          
                                break;
                            }
                            else
                                Close();
                        }
                    }
                    //
                    //
                    //
                    //
                    //
                    //
                    label2.Text = "Ходят : Нолики";
                    break;
                case "Ходят : Нолики":
                    

                    // 5х5
                   
                    // 4х4
                    if (radioButton2.Checked == true & radioButton2.Enabled == false)
                    {
                        if (q.X == pictureBox1.Width / 4)
                            break;
                        if (q.X == pictureBox1.Width / 4 * 2)
                            break;
                        if (q.X == pictureBox1.Width / 4 * 3)
                            break;
                        if (q.Y == pictureBox1.Width / 4)
                            break;
                        if (q.Y == pictureBox1.Width / 4 * 2)
                            break;
                        if (q.Y == pictureBox1.Width / 4 * 3)
                            break;
                        if ((q.X < pictureBox1.Width / 4) && (q.Y < pictureBox1.Width / 4))
                        {
                            if (label3.Text == "1")
                            {
                                g.DrawEllipse(p, 5, 5, pictureBox1.Width / 4 - 10, pictureBox1.Height / 4 - 10);
                                label3.Text = "O";
                            }
                            else
                            {
                                break;
                            }

                        }

                        if ((q.X < pictureBox1.Width / 4) && (q.Y < pictureBox1.Width / 4 * 2) && (q.Y > pictureBox1.Width / 4))
                        {
                            if (label8.Text == "1")
                            {
                                g.DrawEllipse(p, 5, pictureBox1.Height / 4 + 5, pictureBox1.Width / 4 - 10, pictureBox1.Height / 4 - 10);
                                label8.Text = "O";
                            }
                            else
                            {
                                break;
                            }

                        }

                        if ((q.X < pictureBox1.Width / 4) && (q.Y > pictureBox1.Width / 4 * 2) && (q.Y < pictureBox1.Width / 4 * 3))
                        {
                            if (label13.Text == "1")
                            {
                                g.DrawEllipse(p, 5, (pictureBox1.Height / 4) * 2 + 5, pictureBox1.Width / 4 - 10, pictureBox1.Height / 4 - 10);
                                label13.Text = "O";
                            }
                            else
                            {
                                break;
                            }

                        }
                        if ((q.X < pictureBox1.Width / 4) && (q.Y > pictureBox1.Width / 4 * 3))
                        {
                            if (label18.Text == "1")
                            {
                                g.DrawEllipse(p, 5, (pictureBox1.Height / 4) * 3 + 5, pictureBox1.Width / 4 - 10, pictureBox1.Height / 4 - 10);
                                label18.Text = "O";
                            }
                            else
                            {
                                break;
                            }

                        }
                        // 2 stolbik
                        if ((q.X > pictureBox1.Width / 4) && (q.X < (pictureBox1.Width / 4) * 2) && (q.Y < pictureBox1.Width / 4))
                        {
                            if (label4.Text == "1")
                            {
                                g.DrawEllipse(p, pictureBox1.Width / 4 + 5, 5, pictureBox1.Width / 4 - 10, pictureBox1.Height / 4 - 10);
                                label4.Text = "O";
                            }
                            else
                            {
                                break;
                            }

                        }

                        if ((q.X > pictureBox1.Width / 4) && (q.X < (pictureBox1.Width / 4) * 2) && (q.Y < pictureBox1.Width / 4 * 2) && (q.Y > pictureBox1.Width / 4))
                        {
                            if (label9.Text == "1")
                            {
                                g.DrawEllipse(p, pictureBox1.Width / 4 + 5, pictureBox1.Height / 4 + 5, pictureBox1.Width / 4 - 10, pictureBox1.Height / 4 - 10);
                                label9.Text = "O";
                            }
                            else
                            {
                                break;
                            }

                        }

                        if ((q.X > pictureBox1.Width / 4) && (q.X < (pictureBox1.Width / 4) * 2) && (q.Y > pictureBox1.Width / 4 * 2) && (q.Y < pictureBox1.Width / 4 * 3))
                        {
                            if (label14.Text == "1")
                            {
                                g.DrawEllipse(p, pictureBox1.Width / 4 + 5, (pictureBox1.Height / 4) * 2 + 5, pictureBox1.Width / 4 - 10, pictureBox1.Height / 4 - 10);
                                label14.Text = "O";
                            }
                            else
                            {
                                break;
                            }

                        }
                        if ((q.X > pictureBox1.Width / 4) && (q.X < (pictureBox1.Width / 4) * 2) && (q.Y > pictureBox1.Width / 4 * 3))
                        {
                            if (label19.Text == "1")
                            {
                                g.DrawEllipse(p, pictureBox1.Width / 4 + 5, (pictureBox1.Height / 4) * 3 + 5, pictureBox1.Width / 4 - 10, pictureBox1.Height / 4 - 10);
                                label19.Text = "O";
                            }
                            else
                            {
                                break;
                            }

                        }
                        // 3 stolbik
                        if ((q.X > (pictureBox1.Width / 4) * 2) && (q.X < (pictureBox1.Width / 4) * 3) && (q.Y < pictureBox1.Width / 4))
                        {
                            if (label5.Text == "1")
                            {
                                g.DrawEllipse(p, (pictureBox1.Width / 4) * 2 + 5, 5, pictureBox1.Width / 4 - 10, pictureBox1.Height / 4 - 10);
                                label5.Text = "O";
                            }
                            else
                            {
                                break;
                            }

                        }

                        if ((q.X > (pictureBox1.Width / 4) * 2) && (q.X < (pictureBox1.Width / 4) * 3) && (q.Y < pictureBox1.Width / 4 * 2) && (q.Y > pictureBox1.Width / 4))
                        {
                            if (label10.Text == "1")
                            {
                                g.DrawEllipse(p, (pictureBox1.Width / 4) * 2 + 5, pictureBox1.Height / 4 + 5, pictureBox1.Width / 4 - 10, pictureBox1.Height / 4 - 10);
                                label10.Text = "O";
                            }
                            else
                            {
                                break;
                            }

                        }

                        if ((q.X > (pictureBox1.Width / 4) * 2) && (q.X < (pictureBox1.Width / 4) * 3) && (q.Y > pictureBox1.Width / 4 * 2) && (q.Y < pictureBox1.Width / 4 * 3))
                        {
                            if (label15.Text == "1")
                            {
                                g.DrawEllipse(p, (pictureBox1.Width / 4) * 2 + 5, (pictureBox1.Height / 4) * 2 + 5, pictureBox1.Width / 4 - 10, pictureBox1.Height / 4 - 10);
                                label15.Text = "O";
                            }
                            else
                            {
                                break;
                            }

                        }
                        if ((q.X > (pictureBox1.Width / 4) * 2) && (q.X < (pictureBox1.Width / 4) * 3) && (q.Y > pictureBox1.Width / 4 * 3))
                        {
                            if (label20.Text == "1")
                            {
                                g.DrawEllipse(p, (pictureBox1.Width / 4) * 2 + 5, (pictureBox1.Height / 4) * 3 + 5, pictureBox1.Width / 4 - 10, pictureBox1.Height / 4 - 10);
                                label20.Text = "O";
                            }
                            else
                            {
                                break;
                            }

                        }
                        //4 stolbik
                        if ((q.X > (pictureBox1.Width / 4) * 3) && (q.Y < pictureBox1.Width / 4))
                        {
                            if (label6.Text == "1")
                            {
                                g.DrawEllipse(p, (pictureBox1.Width / 4) * 3 + 5, 5, pictureBox1.Width / 4 - 10, pictureBox1.Height / 4 - 10);
                                label6.Text = "O";
                            }
                            else
                            {
                                break;
                            }

                        }

                        if ((q.X > (pictureBox1.Width / 4) * 3) && (q.Y < pictureBox1.Width / 4 * 2) && (q.Y > pictureBox1.Width / 4))
                        {
                            if (label11.Text == "1")
                            {
                                g.DrawEllipse(p, (pictureBox1.Width / 4) * 3 + 5, pictureBox1.Height / 4 + 5, pictureBox1.Width / 4 - 10, pictureBox1.Height / 4 - 10);
                                label11.Text = "O";
                            }
                            else
                            {
                                break;
                            }

                        }

                        if ((q.X > (pictureBox1.Width / 4) * 3) && (q.Y > pictureBox1.Width / 4 * 2) && (q.Y < pictureBox1.Width / 4 * 3))
                        {
                            if (label16.Text == "1")
                            {
                                g.DrawEllipse(p, (pictureBox1.Width / 4) * 3 + 5, (pictureBox1.Height / 4) * 2 + 5, pictureBox1.Width / 4 - 10, pictureBox1.Height / 4 - 10);
                                label16.Text = "O";
                            }
                            else
                            {
                                break;
                            }

                        }
                        if ((q.X > (pictureBox1.Width / 4) * 3) && (q.Y > pictureBox1.Width / 4 * 3))
                        {
                            if (label21.Text == "1")
                            {
                                g.DrawEllipse(p, (pictureBox1.Width / 4) * 3 + 5, (pictureBox1.Height / 4) * 3 + 5, pictureBox1.Width / 4 - 10, pictureBox1.Height / 4 - 10);
                                label21.Text = "O";
                            }
                            else
                            {
                                break;
                            }

                        }
                        int j3;
                        int j4;
                        int j5;
                        int j6;
                        int j7;
                        int j8;
                        int j9;
                        int j10;
                        int j11;
                        int j12;
                        int j13;
                        int j14;
                        int j15;
                        int j16;
                        int j17;
                        int j18;
                        int j19;
                        int j20;
                        int j21;
                        int j22;
                        int j23;
                        int j24;
                        int j25;
                        int j26;
                        int j27;
                        Int32.TryParse(label3.Text, out j3);
                        Int32.TryParse(label4.Text, out j4);
                        Int32.TryParse(label5.Text, out j5);
                        Int32.TryParse(label6.Text, out j6);
                        Int32.TryParse(label7.Text, out j7);
                        Int32.TryParse(label8.Text, out j8);
                        Int32.TryParse(label9.Text, out j9);
                        Int32.TryParse(label10.Text, out j10);
                        Int32.TryParse(label11.Text, out j11);
                        Int32.TryParse(label12.Text, out j12);
                        Int32.TryParse(label13.Text, out j13);
                        Int32.TryParse(label14.Text, out j14);
                        Int32.TryParse(label15.Text, out j15);
                        Int32.TryParse(label16.Text, out j16);
                        Int32.TryParse(label17.Text, out j17);
                        Int32.TryParse(label18.Text, out j18);
                        Int32.TryParse(label19.Text, out j19);
                        Int32.TryParse(label20.Text, out j20);
                        Int32.TryParse(label21.Text, out j21);
                        Int32.TryParse(label22.Text, out j22);
                        Int32.TryParse(label23.Text, out j23);
                        Int32.TryParse(label24.Text, out j24);
                        Int32.TryParse(label25.Text, out j25);
                        Int32.TryParse(label26.Text, out j26);
                        Int32.TryParse(label27.Text, out j27);
                        if ((j6 == 0) && (j10 == 0) && (j14 == 0) && (j18 == 0))
                        {
                            MessageBox.Show("Победили нолики");
                            DialogResult result = MessageBox.Show("Вы хотите сыграть еще раз", "Новая игра", MessageBoxButtons.YesNo, MessageBoxIcon.Question);
                            if (result == DialogResult.Yes)
                            {
                                pictureBox1.Image = Properties.Resources._2;
                                label2.Text = "Ожидание начала игры";
                                label3.Text = "1";
                                label4.Text = "1";
                                label5.Text = "1";
                                label6.Text = "1";
                                label7.Text = "1";
                                label8.Text = "1";
                                label9.Text = "1";
                                label10.Text = "1";
                                label11.Text = "1";
                                label12.Text = "1";
                                label13.Text = "1";
                                label14.Text = "1";
                                label15.Text = "1";
                                label16.Text = "1";
                                label17.Text = "1";
                                label18.Text = "1";
                                label19.Text = "1";
                                label20.Text = "1";
                                label21.Text = "1";
                                label22.Text = "1";
                                label23.Text = "1";
                                label24.Text = "1";
                                label25.Text = "1";
                                label26.Text = "1";
                                label27.Text = "1";
                                radioButton1.Checked = false;
                                radioButton2.Checked = false;
                                radioButton3.Checked = false;
                                checkBox1.Checked = false;
                                button1.Enabled = true;
                                button2.Enabled = false;
                                radioButton1.Enabled = true;
                                radioButton2.Enabled = true;
                                radioButton3.Enabled = true;
                                checkBox1.Enabled = true;
                            
                                break;
                            }
                            else
                                Close();
                        }
                        if ((j3 == 0) && (j9 == 0) && (j15 == 0) && (j21 == 0))
                        {
                            MessageBox.Show("Победили нолики");
                            DialogResult result = MessageBox.Show("Вы хотите сыграть еще раз", "Новая игра", MessageBoxButtons.YesNo, MessageBoxIcon.Question);
                            if (result == DialogResult.Yes)
                            {
                                pictureBox1.Image = Properties.Resources._2;
                                label2.Text = "Ожидание начала игры";
                                label3.Text = "1";
                                label4.Text = "1";
                                label5.Text = "1";
                                label6.Text = "1";
                                label7.Text = "1";
                                label8.Text = "1";
                                label9.Text = "1";
                                label10.Text = "1";
                                label11.Text = "1";
                                label12.Text = "1";
                                label13.Text = "1";
                                label14.Text = "1";
                                label15.Text = "1";
                                label16.Text = "1";
                                label17.Text = "1";
                                label18.Text = "1";
                                label19.Text = "1";
                                label20.Text = "1";
                                label21.Text = "1";
                                label22.Text = "1";
                                label23.Text = "1";
                                label24.Text = "1";
                                label25.Text = "1";
                                label26.Text = "1";
                                label27.Text = "1";
                                radioButton1.Checked = false;
                                radioButton2.Checked = false;
                                radioButton3.Checked = false;
                                checkBox1.Checked = false;
                                button1.Enabled = true;
                                button2.Enabled = false;
                                radioButton1.Enabled = true;
                                radioButton2.Enabled = true;
                                radioButton3.Enabled = true;
                                checkBox1.Enabled = true;
                              
                                break;
                            }
                            else
                                Close();
                        }
                        if ((j6 == 0) && (j11 == 0) && (j16 == 0) && (j21 == 0))
                        {
                            MessageBox.Show("Победили нолики");
                            DialogResult result = MessageBox.Show("Вы хотите сыграть еще раз", "Новая игра", MessageBoxButtons.YesNo, MessageBoxIcon.Question);
                            if (result == DialogResult.Yes)
                            {
                                pictureBox1.Image = Properties.Resources._2;
                                label2.Text = "Ожидание начала игры";
                                label3.Text = "1";
                                label4.Text = "1";
                                label5.Text = "1";
                                label6.Text = "1";
                                label7.Text = "1";
                                label8.Text = "1";
                                label9.Text = "1";
                                label10.Text = "1";
                                label11.Text = "1";
                                label12.Text = "1";
                                label13.Text = "1";
                                label14.Text = "1";
                                label15.Text = "1";
                                label16.Text = "1";
                                label17.Text = "1";
                                label18.Text = "1";
                                label19.Text = "1";
                                label20.Text = "1";
                                label21.Text = "1";
                                label22.Text = "1";
                                label23.Text = "1";
                                label24.Text = "1";
                                label25.Text = "1";
                                label26.Text = "1";
                                label27.Text = "1";
                                radioButton1.Checked = false;
                                radioButton2.Checked = false;
                                radioButton3.Checked = false;
                                checkBox1.Checked = false;
                                button1.Enabled = true;
                                button2.Enabled = false;
                                radioButton1.Enabled = true;
                                radioButton2.Enabled = true;
                                radioButton3.Enabled = true;
                                checkBox1.Enabled = true;
                         
                                break;
                            }
                            else
                                Close();
                        }
                        if ((j5 == 0) && (j10 == 0) && (j15 == 0) && (j20 == 0))
                        {
                            MessageBox.Show("Победили нолики");
                            DialogResult result = MessageBox.Show("Вы хотите сыграть еще раз", "Новая игра", MessageBoxButtons.YesNo, MessageBoxIcon.Question);
                            if (result == DialogResult.Yes)
                            {
                                pictureBox1.Image = Properties.Resources._2;
                                label2.Text = "Ожидание начала игры";
                                label3.Text = "1";
                                label4.Text = "1";
                                label5.Text = "1";
                                label6.Text = "1";
                                label7.Text = "1";
                                label8.Text = "1";
                                label9.Text = "1";
                                label10.Text = "1";
                                label11.Text = "1";
                                label12.Text = "1";
                                label13.Text = "1";
                                label14.Text = "1";
                                label15.Text = "1";
                                label16.Text = "1";
                                label17.Text = "1";
                                label18.Text = "1";
                                label19.Text = "1";
                                label20.Text = "1";
                                label21.Text = "1";
                                label22.Text = "1";
                                label23.Text = "1";
                                label24.Text = "1";
                                label25.Text = "1";
                                label26.Text = "1";
                                label27.Text = "1";
                                radioButton1.Checked = false;
                                radioButton2.Checked = false;
                                radioButton3.Checked = false;
                                checkBox1.Checked = false;
                                button1.Enabled = true;
                                button2.Enabled = false;
                                radioButton1.Enabled = true;
                                radioButton2.Enabled = true;
                                radioButton3.Enabled = true;
                                checkBox1.Enabled = true;
                           
                                break;
                            }
                            else
                                Close();
                        }
                        if ((j4 == 0) && (j9 == 0) && (j14 == 0) && (j19 == 0))
                        {
                            MessageBox.Show("Победили нолики");
                            DialogResult result = MessageBox.Show("Вы хотите сыграть еще раз", "Новая игра", MessageBoxButtons.YesNo, MessageBoxIcon.Question);
                            if (result == DialogResult.Yes)
                            {
                                pictureBox1.Image = Properties.Resources._2;
                                label2.Text = "Ожидание начала игры";
                                label3.Text = "1";
                                label4.Text = "1";
                                label5.Text = "1";
                                label6.Text = "1";
                                label7.Text = "1";
                                label8.Text = "1";
                                label9.Text = "1";
                                label10.Text = "1";
                                label11.Text = "1";
                                label12.Text = "1";
                                label13.Text = "1";
                                label14.Text = "1";
                                label15.Text = "1";
                                label16.Text = "1";
                                label17.Text = "1";
                                label18.Text = "1";
                                label19.Text = "1";
                                label20.Text = "1";
                                label21.Text = "1";
                                label22.Text = "1";
                                label23.Text = "1";
                                label24.Text = "1";
                                label25.Text = "1";
                                label26.Text = "1";
                                label27.Text = "1";
                                radioButton1.Checked = false;
                                radioButton2.Checked = false;
                                radioButton3.Checked = false;
                                checkBox1.Checked = false;
                                button1.Enabled = true;
                                button2.Enabled = false;
                                radioButton1.Enabled = true;
                                radioButton2.Enabled = true;
                                radioButton3.Enabled = true;
                                checkBox1.Enabled = true;
                          
                                break;
                            }
                            else
                                Close();
                        }
                        if ((j3 == 0) && (j8 == 0) && (j13 == 0) && (j18 == 0))
                        {
                            MessageBox.Show("Победили нолики");
                            DialogResult result = MessageBox.Show("Вы хотите сыграть еще раз", "Новая игра", MessageBoxButtons.YesNo, MessageBoxIcon.Question);
                            if (result == DialogResult.Yes)
                            {
                                pictureBox1.Image = Properties.Resources._2;
                                label2.Text = "Ожидание начала игры";
                                label3.Text = "1";
                                label4.Text = "1";
                                label5.Text = "1";
                                label6.Text = "1";
                                label7.Text = "1";
                                label8.Text = "1";
                                label9.Text = "1";
                                label10.Text = "1";
                                label11.Text = "1";
                                label12.Text = "1";
                                label13.Text = "1";
                                label14.Text = "1";
                                label15.Text = "1";
                                label16.Text = "1";
                                label17.Text = "1";
                                label18.Text = "1";
                                label19.Text = "1";
                                label20.Text = "1";
                                label21.Text = "1";
                                label22.Text = "1";
                                label23.Text = "1";
                                label24.Text = "1";
                                label25.Text = "1";
                                label26.Text = "1";
                                label27.Text = "1";
                                radioButton1.Checked = false;
                                radioButton2.Checked = false;
                                radioButton3.Checked = false;
                                checkBox1.Checked = false;
                                button1.Enabled = true;
                                button2.Enabled = false;
                                radioButton1.Enabled = true;
                                radioButton2.Enabled = true;
                                radioButton3.Enabled = true;
                                checkBox1.Enabled = true;
                            
                                break;
                            }
                            else
                                Close();
                        }
                        if ((j18 == 0) && (j19 == 0) && (j20 == 0) && (j21 == 0))
                        {
                            MessageBox.Show("Победили нолики");
                            DialogResult result = MessageBox.Show("Вы хотите сыграть еще раз", "Новая игра", MessageBoxButtons.YesNo, MessageBoxIcon.Question);
                            if (result == DialogResult.Yes)
                            {
                                pictureBox1.Image = Properties.Resources._2;
                                label2.Text = "Ожидание начала игры";
                                label3.Text = "1";
                                label4.Text = "1";
                                label5.Text = "1";
                                label6.Text = "1";
                                label7.Text = "1";
                                label8.Text = "1";
                                label9.Text = "1";
                                label10.Text = "1";
                                label11.Text = "1";
                                label12.Text = "1";
                                label13.Text = "1";
                                label14.Text = "1";
                                label15.Text = "1";
                                label16.Text = "1";
                                label17.Text = "1";
                                label18.Text = "1";
                                label19.Text = "1";
                                label20.Text = "1";
                                label21.Text = "1";
                                label22.Text = "1";
                                label23.Text = "1";
                                label24.Text = "1";
                                label25.Text = "1";
                                label26.Text = "1";
                                label27.Text = "1";
                                radioButton1.Checked = false;
                                radioButton2.Checked = false;
                                radioButton3.Checked = false;
                                checkBox1.Checked = false;
                                button1.Enabled = true;
                                button2.Enabled = false;
                                radioButton1.Enabled = true;
                                radioButton2.Enabled = true;
                                radioButton3.Enabled = true;
                                checkBox1.Enabled = true;
                                
                                break;
                            }
                            else
                                Close();
                        }
                        if ((j13 == 0) && (j14 == 0) && (j15 == 0) && (j16 == 0))
                        {
                            MessageBox.Show("Победили нолики");
                            DialogResult result = MessageBox.Show("Вы хотите сыграть еще раз", "Новая игра", MessageBoxButtons.YesNo, MessageBoxIcon.Question);
                            if (result == DialogResult.Yes)
                            {
                                pictureBox1.Image = Properties.Resources._2;
                                label2.Text = "Ожидание начала игры";
                                label3.Text = "1";
                                label4.Text = "1";
                                label5.Text = "1";
                                label6.Text = "1";
                                label7.Text = "1";
                                label8.Text = "1";
                                label9.Text = "1";
                                label10.Text = "1";
                                label11.Text = "1";
                                label12.Text = "1";
                                label13.Text = "1";
                                label14.Text = "1";
                                label15.Text = "1";
                                label16.Text = "1";
                                label17.Text = "1";
                                label18.Text = "1";
                                label19.Text = "1";
                                label20.Text = "1";
                                label21.Text = "1";
                                label22.Text = "1";
                                label23.Text = "1";
                                label24.Text = "1";
                                label25.Text = "1";
                                label26.Text = "1";
                                label27.Text = "1";
                                radioButton1.Checked = false;
                                radioButton2.Checked = false;
                                radioButton3.Checked = false;
                                checkBox1.Checked = false;
                                button1.Enabled = true;
                                button2.Enabled = false;
                                radioButton1.Enabled = true;
                                radioButton2.Enabled = true;
                                radioButton3.Enabled = true;
                                checkBox1.Enabled = true;
                          
                                break;
                            }
                            else
                                Close();
                        }
                        if ((j8 == 0) && (j9 == 0) && (j10 == 0) && (j11 == 0))
                        {
                            MessageBox.Show("Победили нолики");
                            DialogResult result = MessageBox.Show("Вы хотите сыграть еще раз", "Новая игра", MessageBoxButtons.YesNo, MessageBoxIcon.Question);
                            if (result == DialogResult.Yes)
                            {
                                pictureBox1.Image = Properties.Resources._2;
                                label2.Text = "Ожидание начала игры";
                                label3.Text = "1";
                                label4.Text = "1";
                                label5.Text = "1";
                                label6.Text = "1";
                                label7.Text = "1";
                                label8.Text = "1";
                                label9.Text = "1";
                                label10.Text = "1";
                                label11.Text = "1";
                                label12.Text = "1";
                                label13.Text = "1";
                                label14.Text = "1";
                                label15.Text = "1";
                                label16.Text = "1";
                                label17.Text = "1";
                                label18.Text = "1";
                                label19.Text = "1";
                                label20.Text = "1";
                                label21.Text = "1";
                                label22.Text = "1";
                                label23.Text = "1";
                                label24.Text = "1";
                                label25.Text = "1";
                                label26.Text = "1";
                                label27.Text = "1";
                                radioButton1.Checked = false;
                                radioButton2.Checked = false;
                                radioButton3.Checked = false;
                                checkBox1.Checked = false;
                                button1.Enabled = true;
                                button2.Enabled = false;
                                radioButton1.Enabled = true;
                                radioButton2.Enabled = true;
                                radioButton3.Enabled = true;
                                checkBox1.Enabled = true;
                         
                                break;
                            }
                            else
                                Close();
                        }
                        if ((j3 == 0) && (j4 == 0) && (j5 == 0) && (j6 == 0))
                        {
                            MessageBox.Show("Победили нолики");
                            DialogResult result = MessageBox.Show("Вы хотите сыграть еще раз", "Новая игра", MessageBoxButtons.YesNo, MessageBoxIcon.Question);
                            if (result == DialogResult.Yes)
                            {
                                pictureBox1.Image = Properties.Resources._2;
                                label2.Text = "Ожидание начала игры";
                                label3.Text = "1";
                                label4.Text = "1";
                                label5.Text = "1";
                                label6.Text = "1";
                                label7.Text = "1";
                                label8.Text = "1";
                                label9.Text = "1";
                                label10.Text = "1";
                                label11.Text = "1";
                                label12.Text = "1";
                                label13.Text = "1";
                                label14.Text = "1";
                                label15.Text = "1";
                                label16.Text = "1";
                                label17.Text = "1";
                                label18.Text = "1";
                                label19.Text = "1";
                                label20.Text = "1";
                                label21.Text = "1";
                                label22.Text = "1";
                                label23.Text = "1";
                                label24.Text = "1";
                                label25.Text = "1";
                                label26.Text = "1";
                                label27.Text = "1";
                                radioButton1.Checked = false;
                                radioButton2.Checked = false;
                                radioButton3.Checked = false;
                                checkBox1.Checked = false;
                                button1.Enabled = true;
                                button2.Enabled = false;
                                radioButton1.Enabled = true;
                                radioButton2.Enabled = true;
                                radioButton3.Enabled = true;
                                checkBox1.Enabled = true;
                      
                                break;
                            }
                            else
                                Close();
                        }
                        if (j3 != 1 && j4 != 1 && j5 != 1 && j8 != 1 && j9 != 1 && j10 != 1 && j13 != 1 && j14 != 1 && j15 != 1 && j6 != 1 && j11 != 1 && j16 != 1 && j21 != 1 && j18 != 1 && j19 != 1 && j20 != 1)
                        {
                            MessageBox.Show("Ничья");
                            DialogResult result = MessageBox.Show("Вы хотите сыграть еще раз", "Новая игра", MessageBoxButtons.YesNo, MessageBoxIcon.Question);
                            if (result == DialogResult.Yes)
                            {
                                pictureBox1.Image = Properties.Resources._2;
                                label2.Text = "Ожидание начала игры";
                                label3.Text = "1";
                                label4.Text = "1";
                                label5.Text = "1";
                                label6.Text = "1";
                                label7.Text = "1";
                                label8.Text = "1";
                                label9.Text = "1";
                                label10.Text = "1";
                                label11.Text = "1";
                                label12.Text = "1";
                                label13.Text = "1";
                                label14.Text = "1";
                                label15.Text = "1";
                                label16.Text = "1";
                                label17.Text = "1";
                                label18.Text = "1";
                                label19.Text = "1";
                                label20.Text = "1";
                                label21.Text = "1";
                                label22.Text = "1";
                                label23.Text = "1";
                                label24.Text = "1";
                                label25.Text = "1";
                                label26.Text = "1";
                                label27.Text = "1";
                                radioButton1.Checked = false;
                                radioButton2.Checked = false;
                                radioButton3.Checked = false;
                                checkBox1.Checked = false;
                                button1.Enabled = true;
                                button2.Enabled = false;
                                radioButton1.Enabled = true;
                                radioButton2.Enabled = true;
                                radioButton3.Enabled = true;
                                checkBox1.Enabled = true;
                                
                                break;
                            }
                            else
                                Close();
                        }
                    }
                    // 3х3
                    if (radioButton1.Checked == true & radioButton1.Enabled == false)
                    {
                        if (q.X == pictureBox1.Width / 3)
                            break;
                        if (q.X == pictureBox1.Width / 3 * 2)
                            break;
                        if (q.Y == pictureBox1.Width / 3)
                            break;
                        if (q.Y == pictureBox1.Width / 3 * 2)
                            break;
                        if ((q.X < pictureBox1.Width / 3) && (q.Y < pictureBox1.Width / 3))
                        {
                            if (label3.Text == "1")
                            {
                                g.DrawEllipse(p, 5, 5, pictureBox1.Width / 3 - 10, pictureBox1.Height / 3 - 10);
                                label3.Text = "O";
                            }
                            else
                            {
                                break;
                            }

                        }

                        if ((q.X < pictureBox1.Width / 3) && (q.Y < pictureBox1.Width / 3 * 2) && (q.Y > pictureBox1.Width / 3))
                        {
                            if (label8.Text == "1")
                            {
                                g.DrawEllipse(p, 5, pictureBox1.Height / 3 + 5, pictureBox1.Width / 3 - 10, pictureBox1.Height / 3 - 10);
                                label8.Text = "O";
                            }
                            else
                            {
                                break;
                            }

                        }

                        if ((q.X < pictureBox1.Width / 3) && (q.Y > pictureBox1.Width / 3 * 2))
                        {
                            if (label13.Text == "1")
                            {
                                g.DrawEllipse(p, 5, (pictureBox1.Height / 3) * 2 + 5, pictureBox1.Width / 3 - 10, pictureBox1.Height / 3 - 10);
                                label13.Text = "O";
                            }
                            else
                            {
                                break;
                            }

                        }
                        // 2 столбик
                        if ((q.X < (pictureBox1.Width / 3) * 2) && (q.X > pictureBox1.Width / 3) && (q.Y < pictureBox1.Width / 3))
                        {
                            if (label4.Text == "1")
                            {
                                g.DrawEllipse(p, pictureBox1.Width / 3 + 5, 5, pictureBox1.Width / 3 - 10, pictureBox1.Height / 3 - 10);
                                label4.Text = "O";
                            }
                            else
                            {
                                break;
                            }

                        }

                        if ((q.X < (pictureBox1.Width / 3) * 2) && (q.X > pictureBox1.Width / 3) && (q.Y < pictureBox1.Width / 3 * 2) && (q.Y > pictureBox1.Width / 3))
                        {
                            if (label9.Text == "1")
                            {
                                g.DrawEllipse(p, pictureBox1.Width / 3 + 5, pictureBox1.Height / 3 + 5, pictureBox1.Width / 3 - 10, pictureBox1.Height / 3 - 10);
                                label9.Text = "O";
                            }
                            else
                            {
                                break;
                            }

                        }

                        if ((q.X < (pictureBox1.Width / 3) * 2) && (q.X > pictureBox1.Width / 3) && (q.Y > pictureBox1.Width / 3 * 2))
                        {
                            if (label14.Text == "1")
                            {
                                g.DrawEllipse(p, pictureBox1.Width / 3 + 5, (pictureBox1.Height / 3) * 2 + 5, pictureBox1.Width / 3 - 10, pictureBox1.Height / 3 - 10);
                                label14.Text = "O";
                            }
                            else
                            {
                                break;
                            }

                        }
                        // 3 столбик
                        if ((q.X > (pictureBox1.Width / 3) * 2) && (q.Y < pictureBox1.Width / 3))
                        {
                            if (label5.Text == "1")
                            {
                                g.DrawEllipse(p, (pictureBox1.Width / 3) * 2 + 5, 5, pictureBox1.Width / 3 - 10, pictureBox1.Height / 3 - 10);
                                label5.Text = "O";
                            }
                            else
                            {
                                break;
                            }

                        }

                        if ((q.X > (pictureBox1.Width / 3) * 2) && (q.Y < pictureBox1.Width / 3 * 2) && (q.Y > pictureBox1.Width / 3))
                        {
                            if (label10.Text == "1")
                            {
                                g.DrawEllipse(p, (pictureBox1.Width / 3) * 2 + 5, pictureBox1.Height / 3 + 5, pictureBox1.Width / 3 - 10, pictureBox1.Height / 3 - 10);
                                label10.Text = "O";
                            }
                            else
                            {
                                break;
                            }

                        }

                        if ((q.X > (pictureBox1.Width / 3) * 2) && (q.Y > pictureBox1.Width / 3 * 2))
                        {
                            if (label15.Text == "1")
                            {
                                g.DrawEllipse(p, (pictureBox1.Width / 3) * 2 + 5, (pictureBox1.Height / 3) * 2 + 5, pictureBox1.Width / 3 - 10, pictureBox1.Height / 3 - 10);
                                label15.Text = "O";
                            }
                            else
                            {
                                break;
                            }
                           

                        }
                        int j3;
                        int j4;
                        int j5;
                        int j6;
                        int j7;
                        int j8;
                        int j9;
                        int j10;
                        int j11;
                        int j12;
                        int j13;
                        int j14;
                        int j15;
                        int j16;
                        int j17;
                        int j18;
                        int j19;
                        int j20;
                        int j21;
                        int j22;
                        int j23;
                        int j24;
                        int j25;
                        int j26;
                        int j27;
                        Int32.TryParse(label3.Text, out j3);
                        Int32.TryParse(label4.Text, out j4);
                        Int32.TryParse(label5.Text, out j5);
                        Int32.TryParse(label6.Text, out j6);
                        Int32.TryParse(label7.Text, out j7);
                        Int32.TryParse(label8.Text, out j8);
                        Int32.TryParse(label9.Text, out j9);
                        Int32.TryParse(label10.Text, out j10);
                        Int32.TryParse(label11.Text, out j11);
                        Int32.TryParse(label12.Text, out j12);
                        Int32.TryParse(label13.Text, out j13);
                        Int32.TryParse(label14.Text, out j14);
                        Int32.TryParse(label15.Text, out j15);
                        Int32.TryParse(label16.Text, out j16);
                        Int32.TryParse(label17.Text, out j17);
                        Int32.TryParse(label18.Text, out j18);
                        Int32.TryParse(label19.Text, out j19);
                        Int32.TryParse(label20.Text, out j20);
                        Int32.TryParse(label21.Text, out j21);
                        Int32.TryParse(label22.Text, out j22);
                        Int32.TryParse(label23.Text, out j23);
                        Int32.TryParse(label24.Text, out j24);
                        Int32.TryParse(label25.Text, out j25);
                        Int32.TryParse(label26.Text, out j26);
                        Int32.TryParse(label27.Text, out j27);
                        if ((j5 == 0) && (j9 == 0) && (j13 == 0))
                        {
                            MessageBox.Show("Победили нолики");
                            DialogResult result = MessageBox.Show("Вы хотите сыграть еще раз", "Новая игра", MessageBoxButtons.YesNo, MessageBoxIcon.Question);
                            if (result == DialogResult.Yes)
                            {
                                pictureBox1.Image = Properties.Resources._2;
                                label2.Text = "Ожидание начала игры";
                                label3.Text = "1";
                                label4.Text = "1";
                                label5.Text = "1";
                                label6.Text = "1";
                                label7.Text = "1";
                                label8.Text = "1";
                                label9.Text = "1";
                                label10.Text = "1";
                                label11.Text = "1";
                                label12.Text = "1";
                                label13.Text = "1";
                                label14.Text = "1";
                                label15.Text = "1";
                                label16.Text = "1";
                                label17.Text = "1";
                                label18.Text = "1";
                                label19.Text = "1";
                                label20.Text = "1";
                                label21.Text = "1";
                                label22.Text = "1";
                                label23.Text = "1";
                                label24.Text = "1";
                                label25.Text = "1";
                                label26.Text = "1";
                                label27.Text = "1";
                                radioButton1.Checked = false;
                                radioButton2.Checked = false;
                                radioButton3.Checked = false;
                                checkBox1.Checked = false;
                                button1.Enabled = true;
                                button2.Enabled = false;
                                radioButton1.Enabled = true;
                                radioButton2.Enabled = true;
                                radioButton3.Enabled = true;
                                checkBox1.Enabled = true;
               
                                break;
                            }
                            else
                                Close();
                        }
                        if ((j3 == 0) && (j9 == 0) && (j15 == 0))
                        {
                            MessageBox.Show("Победили нолики");
                            DialogResult result = MessageBox.Show("Вы хотите сыграть еще раз", "Новая игра", MessageBoxButtons.YesNo, MessageBoxIcon.Question);
                            if (result == DialogResult.Yes)
                            {
                                pictureBox1.Image = Properties.Resources._2;
                                label2.Text = "Ожидание начала игры";
                                label3.Text = "1";
                                label4.Text = "1";
                                label5.Text = "1";
                                label6.Text = "1";
                                label7.Text = "1";
                                label8.Text = "1";
                                label9.Text = "1";
                                label10.Text = "1";
                                label11.Text = "1";
                                label12.Text = "1";
                                label13.Text = "1";
                                label14.Text = "1";
                                label15.Text = "1";
                                label16.Text = "1";
                                label17.Text = "1";
                                label18.Text = "1";
                                label19.Text = "1";
                                label20.Text = "1";
                                label21.Text = "1";
                                label22.Text = "1";
                                label23.Text = "1";
                                label24.Text = "1";
                                label25.Text = "1";
                                label26.Text = "1";
                                label27.Text = "1";
                                radioButton1.Checked = false;
                                radioButton2.Checked = false;
                                radioButton3.Checked = false;
                                checkBox1.Checked = false;
                                button1.Enabled = true;
                                button2.Enabled = false;
                                radioButton1.Enabled = true;
                                radioButton2.Enabled = true;
                                radioButton3.Enabled = true;
                                checkBox1.Enabled = true;
                               
                                break;
                            }
                            else
                                Close();
                        }
                        if ((j5 == 0) && (j10 == 0) && (j15 == 0))
                        {
                            MessageBox.Show("Победили нолики");
                            DialogResult result = MessageBox.Show("Вы хотите сыграть еще раз", "Новая игра", MessageBoxButtons.YesNo, MessageBoxIcon.Question);
                            if (result == DialogResult.Yes)
                            {
                                pictureBox1.Image = Properties.Resources._2;
                                label2.Text = "Ожидание начала игры";
                                label3.Text = "1";
                                label4.Text = "1";
                                label5.Text = "1";
                                label6.Text = "1";
                                label7.Text = "1";
                                label8.Text = "1";
                                label9.Text = "1";
                                label10.Text = "1";
                                label11.Text = "1";
                                label12.Text = "1";
                                label13.Text = "1";
                                label14.Text = "1";
                                label15.Text = "1";
                                label16.Text = "1";
                                label17.Text = "1";
                                label18.Text = "1";
                                label19.Text = "1";
                                label20.Text = "1";
                                label21.Text = "1";
                                label22.Text = "1";
                                label23.Text = "1";
                                label24.Text = "1";
                                label25.Text = "1";
                                label26.Text = "1";
                                label27.Text = "1";
                                radioButton1.Checked = false;
                                radioButton2.Checked = false;
                                radioButton3.Checked = false;
                                checkBox1.Checked = false;
                                button1.Enabled = true;
                                button2.Enabled = false;
                                radioButton1.Enabled = true;
                                radioButton2.Enabled = true;
                                radioButton3.Enabled = true;
                                checkBox1.Enabled = true;
                            
                                break;
                            }
                            else
                                Close();
                        }
                        if ((j4 == 0) && (j9 == 0) && (j14 == 0))
                        {
                            MessageBox.Show("Победили нолики");
                            DialogResult result = MessageBox.Show("Вы хотите сыграть еще раз", "Новая игра", MessageBoxButtons.YesNo, MessageBoxIcon.Question);
                            if (result == DialogResult.Yes)
                            {
                                pictureBox1.Image = Properties.Resources._2;
                                label2.Text = "Ожидание начала игры";
                                label3.Text = "1";
                                label4.Text = "1";
                                label5.Text = "1";
                                label6.Text = "1";
                                label7.Text = "1";
                                label8.Text = "1";
                                label9.Text = "1";
                                label10.Text = "1";
                                label11.Text = "1";
                                label12.Text = "1";
                                label13.Text = "1";
                                label14.Text = "1";
                                label15.Text = "1";
                                label16.Text = "1";
                                label17.Text = "1";
                                label18.Text = "1";
                                label19.Text = "1";
                                label20.Text = "1";
                                label21.Text = "1";
                                label22.Text = "1";
                                label23.Text = "1";
                                label24.Text = "1";
                                label25.Text = "1";
                                label26.Text = "1";
                                label27.Text = "1";
                                radioButton1.Checked = false;
                                radioButton2.Checked = false;
                                radioButton3.Checked = false;
                                checkBox1.Checked = false;
                                button1.Enabled = true;
                                button2.Enabled = false;
                                radioButton1.Enabled = true;
                                radioButton2.Enabled = true;
                                radioButton3.Enabled = true;
                                checkBox1.Enabled = true;
                        
                                break;
                            }
                            else
                                Close();
                        }
                        if ((j3 == 0) && (j8 == 0) && (j13 == 0))
                        {
                            MessageBox.Show("Победили нолики");
                            DialogResult result = MessageBox.Show("Вы хотите сыграть еще раз", "Новая игра", MessageBoxButtons.YesNo, MessageBoxIcon.Question);
                            if (result == DialogResult.Yes)
                            {
                                pictureBox1.Image = Properties.Resources._2;
                                label2.Text = "Ожидание начала игры";
                                label3.Text = "1";
                                label4.Text = "1";
                                label5.Text = "1";
                                label6.Text = "1";
                                label7.Text = "1";
                                label8.Text = "1";
                                label9.Text = "1";
                                label10.Text = "1";
                                label11.Text = "1";
                                label12.Text = "1";
                                label13.Text = "1";
                                label14.Text = "1";
                                label15.Text = "1";
                                label16.Text = "1";
                                label17.Text = "1";
                                label18.Text = "1";
                                label19.Text = "1";
                                label20.Text = "1";
                                label21.Text = "1";
                                label22.Text = "1";
                                label23.Text = "1";
                                label24.Text = "1";
                                label25.Text = "1";
                                label26.Text = "1";
                                label27.Text = "1";
                                radioButton1.Checked = false;
                                radioButton2.Checked = false;
                                radioButton3.Checked = false;
                                checkBox1.Checked = false;
                                button1.Enabled = true;
                                button2.Enabled = false;
                                radioButton1.Enabled = true;
                                radioButton2.Enabled = true;
                                radioButton3.Enabled = true;
                                checkBox1.Enabled = true;
                        
                                break;
                            }
                            else
                                Close();
                        }
                        if ((j13 == 0) && (j14 == 0) && (j15 == 0))
                        {
                            MessageBox.Show("Победили нолики");
                            DialogResult result = MessageBox.Show("Вы хотите сыграть еще раз", "Новая игра", MessageBoxButtons.YesNo, MessageBoxIcon.Question);
                            if (result == DialogResult.Yes)
                            {
                                pictureBox1.Image = Properties.Resources._2;
                                label2.Text = "Ожидание начала игры";
                                label3.Text = "1";
                                label4.Text = "1";
                                label5.Text = "1";
                                label6.Text = "1";
                                label7.Text = "1";
                                label8.Text = "1";
                                label9.Text = "1";
                                label10.Text = "1";
                                label11.Text = "1";
                                label12.Text = "1";
                                label13.Text = "1";
                                label14.Text = "1";
                                label15.Text = "1";
                                label16.Text = "1";
                                label17.Text = "1";
                                label18.Text = "1";
                                label19.Text = "1";
                                label20.Text = "1";
                                label21.Text = "1";
                                label22.Text = "1";
                                label23.Text = "1";
                                label24.Text = "1";
                                label25.Text = "1";
                                label26.Text = "1";
                                label27.Text = "1";
                                radioButton1.Checked = false;
                                radioButton2.Checked = false;
                                radioButton3.Checked = false;
                                checkBox1.Checked = false;
                                button1.Enabled = true;
                                button2.Enabled = false;
                                radioButton1.Enabled = true;
                                radioButton2.Enabled = true;
                                radioButton3.Enabled = true;
                                checkBox1.Enabled = true;
                           
                                break;
                            }
                            else
                                Close();
                        }
                        if ((j8 == 0) && (j9 == 0) && (j10 == 0))
                        {
                            MessageBox.Show("Победили нолики");
                            DialogResult result = MessageBox.Show("Вы хотите сыграть еще раз", "Новая игра", MessageBoxButtons.YesNo, MessageBoxIcon.Question);
                            if (result == DialogResult.Yes)
                            {
                                pictureBox1.Image = Properties.Resources._2;
                                label2.Text = "Ожидание начала игры";
                                label3.Text = "1";
                                label4.Text = "1";
                                label5.Text = "1";
                                label6.Text = "1";
                                label7.Text = "1";
                                label8.Text = "1";
                                label9.Text = "1";
                                label10.Text = "1";
                                label11.Text = "1";
                                label12.Text = "1";
                                label13.Text = "1";
                                label14.Text = "1";
                                label15.Text = "1";
                                label16.Text = "1";
                                label17.Text = "1";
                                label18.Text = "1";
                                label19.Text = "1";
                                label20.Text = "1";
                                label21.Text = "1";
                                label22.Text = "1";
                                label23.Text = "1";
                                label24.Text = "1";
                                label25.Text = "1";
                                label26.Text = "1";
                                label27.Text = "1";
                                radioButton1.Checked = false;
                                radioButton2.Checked = false;
                                radioButton3.Checked = false;
                                checkBox1.Checked = false;
                                button1.Enabled = true;
                                button2.Enabled = false;
                                radioButton1.Enabled = true;
                                radioButton2.Enabled = true;
                                radioButton3.Enabled = true;
                                checkBox1.Enabled = true;
                          
                                break;
                            }
                            else
                                Close();
                        }
                        if ((j3 == 0) && (j4 == 0) && (j5 == 0))
                        {
                            MessageBox.Show("Победили нолики");
                            DialogResult result = MessageBox.Show("Вы хотите сыграть еще раз", "Новая игра", MessageBoxButtons.YesNo, MessageBoxIcon.Question);
                            if (result == DialogResult.Yes)
                            {
                                pictureBox1.Image = Properties.Resources._2;
                                label2.Text = "Ожидание начала игры";
                                label3.Text = "1";
                                label4.Text = "1";
                                label5.Text = "1";
                                label6.Text = "1";
                                label7.Text = "1";
                                label8.Text = "1";
                                label9.Text = "1";
                                label10.Text = "1";
                                label11.Text = "1";
                                label12.Text = "1";
                                label13.Text = "1";
                                label14.Text = "1";
                                label15.Text = "1";
                                label16.Text = "1";
                                label17.Text = "1";
                                label18.Text = "1";
                                label19.Text = "1";
                                label20.Text = "1";
                                label21.Text = "1";
                                label22.Text = "1";
                                label23.Text = "1";
                                label24.Text = "1";
                                label25.Text = "1";
                                label26.Text = "1";
                                label27.Text = "1";
                                radioButton1.Checked = false;
                                radioButton2.Checked = false;
                                radioButton3.Checked = false;
                                checkBox1.Checked = false;
                                button1.Enabled = true;
                                button2.Enabled = false;
                                radioButton1.Enabled = true;
                                radioButton2.Enabled = true;
                                radioButton3.Enabled = true;
                                checkBox1.Enabled = true;
                          
                                break;
                            }
                            else
                                Close();
                        }
                       
                        if (j3 != 1 && j4 != 1 && j5 != 1 && j8 != 1 && j9 != 1 && j10 != 1 && j13 != 1 && j14 != 1 && j15 != 1)
                        {
                            MessageBox.Show("Ничья");
                            DialogResult result = MessageBox.Show("Вы хотите сыграть еще раз", "Новая игра", MessageBoxButtons.YesNo, MessageBoxIcon.Question);
                            if (result == DialogResult.Yes)
                            {
                                pictureBox1.Image = Properties.Resources._2;
                                label2.Text = "Ожидание начала игры";
                                label3.Text = "1";
                                label4.Text = "1";
                                label5.Text = "1";
                                label6.Text = "1";
                                label7.Text = "1";
                                label8.Text = "1";
                                label9.Text = "1";
                                label10.Text = "1";
                                label11.Text = "1";
                                label12.Text = "1";
                                label13.Text = "1";
                                label14.Text = "1";
                                label15.Text = "1";
                                label16.Text = "1";
                                label17.Text = "1";
                                label18.Text = "1";
                                label19.Text = "1";
                                label20.Text = "1";
                                label21.Text = "1";
                                label22.Text = "1";
                                label23.Text = "1";
                                label24.Text = "1";
                                label25.Text = "1";
                                label26.Text = "1";
                                label27.Text = "1";
                                radioButton1.Checked = false;
                                radioButton2.Checked = false;
                                radioButton3.Checked = false;
                                checkBox1.Checked = false;
                                button1.Enabled = true;
                                button2.Enabled = false;
                                radioButton1.Enabled = true;
                                radioButton2.Enabled = true;
                                radioButton3.Enabled = true;
                                checkBox1.Enabled = true;
                          
                                break;
                            }
                            else
                                Close();
                        }
                    }
                    label2.Text = "Ходят : Крестики";
                        break;
                    }
        }

        private void button2_Click(object sender, EventArgs e)
        {
            if (button1.Enabled == false)
            {
                
                DialogResult result = MessageBox.Show("Вы точно хотите прервать партию?", "Конец игры", MessageBoxButtons.YesNo, MessageBoxIcon.Question);
                if (result == DialogResult.Yes)
                {
                    pictureBox1.Image = Properties.Resources._2;
                    label2.Text = "Ожидание начала игры";
                    label3.Text = "1";
                    label4.Text = "1";
                    label5.Text = "1";
                    label6.Text = "1";
                    label7.Text = "1";
                    label8.Text = "1";
                    label9.Text = "1";
                    label10.Text = "1";
                    label11.Text = "1";
                    label12.Text = "1";
                    label13.Text = "1";
                    label14.Text = "1";
                    label15.Text = "1";
                    label16.Text = "1";
                    label17.Text = "1";
                    label18.Text = "1";
                    label19.Text = "1";
                    label20.Text = "1";
                    label21.Text = "1";
                    label22.Text = "1";
                    label23.Text = "1";
                    label24.Text = "1";
                    label25.Text = "1";
                    label26.Text = "1";
                    label27.Text = "1";
                    radioButton1.Checked = false;
                    radioButton2.Checked = false;
                    radioButton3.Checked = false;
                    checkBox1.Checked = false;
                    button1.Enabled = true;
                    button2.Enabled = false;
                    radioButton1.Enabled = true;
                    radioButton2.Enabled = true;
                    radioButton3.Enabled = true;
                    checkBox1.Enabled = true;
                  
                }
                else
                {
                    return;
                }
            }
        }

        private void button3_Click(object sender, EventArgs e)
        {
            DialogResult result = MessageBox.Show("Вы точно хотите завершить игру?", "Конец игры", MessageBoxButtons.YesNo, MessageBoxIcon.Question);
            if (result == DialogResult.Yes)
                Close();
        }
    }
}

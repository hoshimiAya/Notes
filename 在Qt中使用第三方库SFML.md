# 将SFML引入Qt
基于 Qt Creator 4.11.1 / Qt 5.14.1 / SFML-2.5.1
1. 下载网址 https://www.sfml-dev.org/download.php 。
2. 下载版本选择 GCC 7.3.0 MinGW (DW2) - 32-bit 。
3. 将下载完的文件夹 SFML-2.5.1 解压到任意路径(PATH) (PATH：指 SFML-2.5.1 所在路径)。
4. 在系统环境变量 Path 中加入 (PATH)\SFML-2.5.1\bin 。
5. 在 Qt *.pro文件中加入以下代码

        INCLUDEPATH += (PATH)\SFML-2.5.1\include\
        CONFIG(debug,debug | release )
        {
        LIBS += (PATH)\SFML-2.5.1\lib\
        }
6. 在 main.cpp 中加入头文件

        #include <SFML/Graphics.hpp>
7. 测试代码

        int main()
        {
            sf::RenderWindow window(sf::VideoMode(200, 200), "SFML works!");
            sf::CircleShape shape(100.f);
            shape.setFillColor(sf::Color::Green);

            while (window.isOpen())
            {
                sf::Event event;
                while (window.pollEvent(event))
                {
                    if (event.type == sf::Event::Closed)
                        window.close();
                }
                window.clear();
                window.draw(shape);
                window.display();
            }
            return 0;
        }
Podstawowa paczka skrypt�w ACPL [BETA]

Paczka zawiera: (u�ycie opisane ni�ej)
* Wbudowany VCOMAI w wersji 3.02
* Wbudowany Taskmaster (skrypt do tworzenia briefing�w i zarz�dzania zadaniami)
* Skrypt dodaj�cy automatycznie odpowiedni� ilo�� medykament�w grywalnym jednostk� [z mo�liwo�ci� konfiguracji]
* Skrypt zarz�dzaj�cy wrogiem ustawionym na sta�e w budynkach
* Skrypt pozwalaj�cy wy�wietla� animacje w �rodowisku MP (WIP)
* Skrypt pozwalaj�cy tworzy� zombie-stalker�w
* Skrypt pozwalaj�cy na przejmowanie w�adzy nad HC
* Skrypt pozwalaj�cy na przejmowanie oraz u�ycie artylerii
* Skrypt ustawiaj�cy skill wszystkich jednostek na mapie [z mo�liwo�ci� konfiguracji]
* Skrypt pozwalaj�cy na ustawienie gogli jednostk� graczy (zamiast tych ustawionych w profilu)
* Skrypt pozwalaj�cy na prze�adowanie amunicji z nie pasuj�cych do naszej broni magazynk�w do pasuj�cych do naszej broni magazynk�w [IF44 only!]

CHANGELOG:
*BETA:
- Wydanie paczki, duh

Instalacja:
Zawarto�� paczki wrzucamy do pliku misji, w pliku init.sqf ustawiamy warto�ci w ostatniej linijce dla:
[x1,[x2],x3,x4] execVM "acpl_fncs_init.sqf";
* x1 - wersja teatru, 0 dla modern, 1 dla WW2
* x2 - nazwy pojazd�w medycznych, zapisane w [], np.: [pojazd1,pojazd2]
* x3 - czy w�aczy� VCOMAI, true/false
* x4 - czy zablokowa� mo�liwo�� chodzenia grywalnemu AI (odblokowa� mo�e dow�dca dru�yny w menu ACE'a), true/false

W init.sqf znajduje si� r�wnie� brefing, instrukcja do jego skonfigurowania znajduje si� w shk_taskmaster.sqf

W pliku acpl_fncs_init.sqf mo�emy dodatkowo skonfigurowa� ilo�� medykament�w dla graczy oraz ustawienia VCOMAI

Ustawienia skilla jednostek znajdziemy acpl_fncs\acpl_msc\ustawienia.sqf, skill jest ustawiany dla ka�dej ze stron oddzielnie! Jednostki spawnowane w trakcie rozgrywki r�wnie� podlegaj� modyfikacji.

U�ycie:
> DoStop.sqf [v1.5] - skrypt zarz�dzaj�cy przeciwnikiem ustawionym na sta�e w budynkach:
W init jednostki wklejamy: _nul = [this,pos,ducking] execVM "acpl_fncs\dostop.sqf"; gdzie:

* this - nazwa jednostki
* pos - pozycja w jakiej jednostka ma sta� - "up"/"middle"/"down"
* ducking - czy jednostka ma chowa� si� przed ostrza�em/kiedy prze�adowywuje - true/false

Aby odblokowa� jednostk�, aby np.: wysz�a z budynku nale�y u�y� komendy: nazwa_jednostki setvariable ["acpl_dostop",false,true];
Aby zmieni� pozycje jednostki nale�y u�y� komendy: nazwa_jednostki setvariable ["acpl_dostop_pos",numer,true]; w miejscu numer wpisuj�c numer pozycji - 2 = stoj�ca, 1 = kucaj�ca, 0 = le��ca

> Animations [v1.0] - skrypt pozwalaj�cy ustawi� animacje jednostk�, na razie statycznie (brak funkcji wyj�cia z animacji gdy pod ostrza�em, itd)
W init jednostki wpisujemy: _nul = ["ANIM",[this,"animacja"]] execVM "acpl_fncs\acpl_animations.sqf"; gdzie:

* this - nazwa jednostki
* "animacja" - classname animacji (nale�y u�y� Animation Viewer'a w edytorze aby znale�� klase)

Aby wy�aczy� animacje nale�y u�y� komendy: nazwa_jednostki setVariable ["acpl_animation_active",false,true];

> AddGoogles [v1.0] - skrypt pozwalaj�cy doda� gogle graczowi (zwykle s� one nadpisywane tymi ustawionymi w profilu gracza)
W init jednostki wpisujemy: _nul = [this,"classname"] execVM "acpl_fncs\addgoggles.sqf"; gdzie:

* this - nazwa jednostki
* "classname" - classname gogli

> HC_TakeControl [v1.0] - skrypt pozwalaj�cy na przej�cie kontroli nad High Command pod menu ACE'a
Ustawiamy i konfigurujemy modu�y HC w edytorze. Modu�y nie musz� by� nazwane lecz musz� by� zesob� synchronizowane. Nazwa� nale�y grupy kt�re maj� by� podleg�e HC
W init jednostki wpisujemy _nul = [_unit,[_grps]] execVM "acpl_fncs\HC_takecontrol.sqf"; gdzie:

* _unit - nazwa jednostki kt�ra ma pierwotnie posiada� dost�p do HC
* _grps - nazwy podleg�ych grup

> Take_Arty [v1.0] - skrypt dodaj�cy do twojego oddzia�u artylerie (ustawion� wcze�niej na mapie)
W init wklejamy: _nul = [[_arty1,_arty2],_grp] execVM "acpl_fncs\take_arty.sqf"; gdzie:

* [_arty1,_arty2] - s� to nazwy baterii artyleryjskich
* _grp - nazwa grupy (musi by� nazwana!) do kt�rej aryleria ma by� pierwotnie przypisana

> Stalker_Zombie [v1.0] - skrypt zmieniaj�cy jednostk� w przyg�upie zombie
W init jednostki wklejamy: _nul = [this] execVM "acpl_fncs\stalker_zombie.sqf"; gdzie:

* this - nazwa jednostki
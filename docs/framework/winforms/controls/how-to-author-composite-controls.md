---
title: 'Porady: autoryzowanie formantów złożonych'
ms.date: 03/30/2017
helpviewer_keywords:
- UserControl class [Windows Forms], creating composite controls
- user controls [Windows Forms], creating
- user controls [Windows Forms], inheriting from
- composite controls [Windows Forms], creating
ms.assetid: 79c9cf05-5ab6-4a18-886d-88a64748b098
ms.openlocfilehash: 7abdeae4d19ceb6425f85e3cdd28f565a03d7ea4
ms.sourcegitcommit: dfb2a100cfb4d3902c042f17b3204f49bc7635e7
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/21/2018
ms.locfileid: "46508252"
---
# <a name="how-to-author-composite-controls"></a>Porady: autoryzowanie formantów złożonych
Formanty złożone można zastosować na wiele sposobów. Można tworzyć w ramach projektu aplikacji pulpitu Windows i ich używać tylko na formularze w projekcie. Lub można je tworzyć w projekcie Biblioteka formantów Windows, skompilowanie projektu do zestawu i użyj formantów w innych projektach. Można również dziedziczyć z nich i umożliwia szybkie dostosować je do specjalnych celów dziedziczenie visual.  
  
> [!NOTE]
>  Jeśli chcesz tworzyć kontrolki złożonej do użycia w formularzach sieci Web, zobacz artykuł [tworzenia formanty serwera ASP.NET niestandardowe](https://msdn.microsoft.com/library/fbe26c16-cff4-4089-b3dd-877411f0c0ef).  
>   
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-author-a-composite-control"></a>Tworzenie kontrolki złożonej  
  
1.  Otwórz nowy **aplikacji Windows** projekt o nazwie `DemoControlHost`.  
  
2.  Na **projektu** menu, kliknij przycisk **Dodaj kontrolkę użytkownika**.  
  
3.  W **Dodaj nowy element** okno dialogowe, Dodaj plik klasy (plik .vb lub .cs) nazwę, która ma formant złożony, aby.  
  
4.  Wybierz **Dodaj** przycisk, aby utworzyć plik klasy dla kontrolek złożonych.  
  
5.  Dodawanie formantów z **przybornika** do powierzchni złożonego formantu.  
  
6.  Umieść kod w procedurach zdarzeń, do obsługi zdarzeń wywołanych przez złożonego formantu lub jego formantów składowych.  
  
7.  Zamknij projektanta dla formantu złożonego, a następnie zapisz plik, po wyświetleniu monitu.  
  
8.  Na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**.  
  
     Projekt musi być zbudowany w kolejności, w przypadku kontrolek niestandardowych, które będą wyświetlane na **przybornika**.  
  
9. Użyj **DemoControlHost** karcie **przybornika** dodać wystąpienia kontrolki do `Form1`.  
  
### <a name="to-author-a-control-class-library"></a>Aby utworzyć bibliotekę klas formantów  
  
1.  Otwórz nowy **Biblioteka formantów Windows** projektu.  
  
     Domyślnie projektu zawiera kontrolki złożonej.  
  
2.  Dodaj formanty i kod, zgodnie z opisem w poprzedniej procedurze.  
  
3.  Wybierz kontrolkę, która nie dziedziczy z klasy, aby zmienić i ustawić **Modyfikatory** właściwość tej kontrolki na **prywatnej**.  
  
4.  Skompiluj bibliotekę DLL.  
  
### <a name="to-inherit-from-a-composite-control-in-a-control-class-library"></a>Dziedziczenie z kontrolki złożonej w bibliotece klas formantów  
  
1.  Na **pliku** menu wskaż **Dodaj** i wybierz **nowy projekt** Aby dodać nowy **aplikacji Windows** projektu do rozwiązania.  
  
2.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **odwołania** nowy folder projektu, a następnie wybierz **Dodaj odwołanie** otworzyć **Dodaj odwołanie**okno dialogowe.  
  
3.  Wybierz **projektów** kartę, a następnie kliknij dwukrotnie ikonę kontrolki projektu biblioteki.  
  
4.  Na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**.  
  
5.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt Biblioteka kontroli i wybierz **Dodaj nowy element** z menu skrótów.  
  
6.  Wybierz **dziedziczone kontrolki użytkownika** szablonu z **Dodaj nowy element** okno dialogowe.  
  
7.  W **selektor dziedziczenia** okna dialogowego pole, kliknij dwukrotnie formant ma być dziedziczona z.  
  
     Nowy formant zostanie dodany do projektu.  
  
8.  Otwórz projektanta wizualnego nowego formantu i Dodaj dodatkowe formanty składników.  
  
     Możesz zobaczyć formanty składników, które zostały odziedziczone złożonej kontrolki w bibliotece DLL, a można zmienić właściwości formantów którego **Modyfikatory** właściwość jest **publicznych**. Nie można zmienić właściwości formantu którego **Modyfikatory** właściwość **prywatnej**.  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik: tworzenie kontrolki złożonej za pomocą języka Visual Basic](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-basic.md)  
 [Przewodnik: tworzenie kontrolki złożonej za pomocą języka Visual C#](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-csharp.md)  
 [Przewodnik: dziedziczenie z kontrolki formularzy Windows Forms za pomocą języka Visual Basic](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic.md)  
 [Przewodnik: dziedziczenie z kontrolki formularzy Windows Forms za pomocą języka Visual C#](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)  
 [Zalecenia dotyczące typu kontrolki](../../../../docs/framework/winforms/controls/control-type-recommendations.md)  
 [Instrukcje: tworzenie kontrolek dla formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-author-controls-for-windows-forms.md)  
 [Różne typy kontrolek niestandardowych](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)

---
title: 'Instrukcje: autoryzowanie kontrolek złożonych'
ms.date: 03/30/2017
helpviewer_keywords:
- UserControl class [Windows Forms], creating composite controls
- user controls [Windows Forms], creating
- user controls [Windows Forms], inheriting from
- composite controls [Windows Forms], creating
ms.assetid: 79c9cf05-5ab6-4a18-886d-88a64748b098
ms.openlocfilehash: 8bb630d3fb7e064935440439f2f07816e87c77dc
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59317015"
---
# <a name="how-to-author-composite-controls"></a>Instrukcje: autoryzowanie kontrolek złożonych
Formanty złożone można zastosować na wiele sposobów. Można tworzyć w ramach projektu aplikacji pulpitu Windows i ich używać tylko na formularze w projekcie. Lub można je tworzyć w projekcie Biblioteka formantów Windows, skompilowanie projektu do zestawu i użyj formantów w innych projektach. Można również dziedziczyć z nich i umożliwia szybkie dostosować je do specjalnych celów dziedziczenie visual.  
  
> [!NOTE]
>  Jeśli chcesz tworzyć kontrolki złożonej do użycia w formularzach sieci Web, zobacz artykuł [tworzenia formanty serwera ASP.NET niestandardowe](https://docs.microsoft.com/previous-versions/aspnet/zt27tfhy(v=vs.100)).  
>   
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-author-a-composite-control"></a>Tworzenie kontrolki złożonej  
  
1. Otwórz nowy **aplikacji Windows** projekt o nazwie `DemoControlHost`.  
  
2. Na **projektu** menu, kliknij przycisk **Dodaj kontrolkę użytkownika**.  
  
3. W **Dodaj nowy element** okno dialogowe, Dodaj plik klasy (plik .vb lub .cs) nazwę, która ma formant złożony, aby.  
  
4. Wybierz **Dodaj** przycisk, aby utworzyć plik klasy dla kontrolek złożonych.  
  
5. Dodawanie formantów z **przybornika** do powierzchni złożonego formantu.  
  
6. Umieść kod w procedurach zdarzeń, do obsługi zdarzeń wywołanych przez złożonego formantu lub jego formantów składowych.  
  
7. Zamknij projektanta dla formantu złożonego, a następnie zapisz plik, po wyświetleniu monitu.  
  
8. Na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**.  
  
     Projekt musi być zbudowany w kolejności, w przypadku kontrolek niestandardowych, które będą wyświetlane na **przybornika**.  
  
9. Użyj **DemoControlHost** karcie **przybornika** dodać wystąpienia kontrolki do `Form1`.  
  
### <a name="to-author-a-control-class-library"></a>Aby utworzyć bibliotekę klas formantów  
  
1. Otwórz nowy **Biblioteka formantów Windows** projektu.  
  
     Domyślnie projektu zawiera kontrolki złożonej.  
  
2. Dodaj formanty i kod, zgodnie z opisem w poprzedniej procedurze.  
  
3. Wybierz kontrolkę, która nie dziedziczy z klasy, aby zmienić i ustawić **Modyfikatory** właściwość tej kontrolki na **prywatnej**.  
  
4. Skompiluj bibliotekę DLL.  
  
### <a name="to-inherit-from-a-composite-control-in-a-control-class-library"></a>Dziedziczenie z kontrolki złożonej w bibliotece klas formantów  
  
1. Na **pliku** menu wskaż **Dodaj** i wybierz **nowy projekt** Aby dodać nowy **aplikacji Windows** projektu do rozwiązania.  
  
2. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **odwołania** nowy folder projektu, a następnie wybierz **Dodaj odwołanie** otworzyć **Dodaj odwołanie**okno dialogowe.  
  
3. Wybierz **projektów** kartę, a następnie kliknij dwukrotnie ikonę kontrolki projektu biblioteki.  
  
4. Na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**.  
  
5. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt Biblioteka kontroli i wybierz **Dodaj nowy element** z menu skrótów.  
  
6. Wybierz **dziedziczone kontrolki użytkownika** szablonu z **Dodaj nowy element** okno dialogowe.  
  
7. W **selektor dziedziczenia** okna dialogowego pole, kliknij dwukrotnie formant ma być dziedziczona z.  
  
     Nowy formant zostanie dodany do projektu.  
  
8. Otwórz projektanta wizualnego nowego formantu i Dodaj dodatkowe formanty składników.  
  
     Możesz zobaczyć formanty składników, które zostały odziedziczone złożonej kontrolki w bibliotece DLL, a można zmienić właściwości formantów którego **Modyfikatory** właściwość jest **publicznych**. Nie można zmienić właściwości formantu którego **Modyfikatory** właściwość **prywatnej**.  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik: tworzenie kontrolki złożonej za pomocą Visual Basic](walkthrough-authoring-a-composite-control-with-visual-basic.md)
- [Przewodnik: tworzenie kontrolki złożonej za pomocą Visual C#](walkthrough-authoring-a-composite-control-with-visual-csharp.md)
- [Przewodnik: dziedziczenie z kontrolki formularzy systemu Windows z Visual Basic](walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic.md)
- [Przewodnik: dziedziczenie z kontrolki formularzy systemu Windows formantu z Visual C#](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)
- [Zalecenia dotyczące typu formantu](control-type-recommendations.md)
- [Instrukcje: kontrolki autoryzacji dla formularzy systemu Windows](how-to-author-controls-for-windows-forms.md)
- [Różne typy formantów niestandardowych](varieties-of-custom-controls.md)

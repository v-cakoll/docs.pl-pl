---
title: 'Wskazówki: automatyczne zapełnianie Przybornika składnikami niestandardowymi'
ms.date: 03/30/2017
helpviewer_keywords:
- IToolboxService interface
- Toolbox [Windows Forms], populating
- custom components [Windows Forms], adding to Toolbox
ms.assetid: 2fa1e3e8-6b9f-42b2-97c0-2be57444dba4
ms.openlocfilehash: d446ab84cfe135e56483b8b309b696f7f15044fa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33540049"
---
# <a name="walkthrough-automatically-populating-the-toolbox-with-custom-components"></a>Wskazówki: automatyczne zapełnianie Przybornika składnikami niestandardowymi
Jeśli składniki są zdefiniowane przez projekt w aktualnie otwarte rozwiązanie, będzie automatycznie wyświetlane w **przybornika**, z trzeba wykonywać żadnych czynności przez użytkownika. Można też ręcznie wypełnić **przybornika** Twojego składnikami niestandardowymi za pomocą [wybierz przybornika elementy — okno dialogowe (Visual Studio)](http://msdn.microsoft.com/library/bd07835f-18a8-433e-bccc-7141f65263bb), ale **przybornika** uwzględnia elementów rozwiązania kompilacji dane wyjściowe o następującej charakterystyce:  
  
-   Implementuje <xref:System.ComponentModel.IComponent>;  
  
-   Nie ma <xref:System.ComponentModel.ToolboxItemAttribute> ustawioną `false`;  
  
-   Nie ma <xref:System.ComponentModel.DesignTimeVisibleAttribute> ustawioną `false`.  
  
> [!NOTE]
>  **Przybornika** nie jest zgodna z łańcuchów odwołanie, nie będzie on wyświetlany elementy, które nie są tworzone przez projekt w rozwiązaniu.  
  
 W tym przewodniku pokazano, jak niestandardowy składnik zostanie automatycznie wyświetlony w **przybornika** po utworzeniu składnika. Zadania przedstawione w tym przewodniku obejmują:  
  
-   Tworzenie projektu formularzy systemu Windows.  
  
-   Tworzenie niestandardowych składników.  
  
-   Utworzenie wystąpienia składnika niestandardowego.  
  
-   Zwolnienie i ponowne załadowanie niestandardowych składników.  
  
 Gdy skończysz, zostanie wyświetlone **przybornika** jest wypełniane przy użyciu składnika, który został utworzony.  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="creating-the-project"></a>Tworzenie projektu  
 Pierwszym krokiem jest utworzenie projektu i konfigurowanie formularza.  
  
#### <a name="to-create-the-project"></a>Aby utworzyć projekt  
  
1.  Utwórz projekt aplikacji systemu Windows o nazwie `ToolboxExample`.  
  
     Aby uzyskać więcej informacji, zobacz [porady: Tworzenie projektu aplikacji Windows](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa).  
  
2.  Dodaj nowy składnik do projektu. Wywołać ją `DemoComponent`.  
  
     Aby uzyskać więcej informacji, zobacz [NIB: porady: dodawanie nowych elementów projektu](http://msdn.microsoft.com/library/63d3e16b-de6e-4bb5-a0e3-ecec762201ce).  
  
3.  Skompiluj projekt.  
  
4.  Z **narzędzia** menu, kliknij przycisk **opcje** elementu. Kliknij przycisk **ogólne** w obszarze **Projektant formularzy systemu Windows** element i upewnij się, że **AutoToolboxPopulate** ustawiono opcję **True**.  
  
## <a name="creating-an-instance-of-a-custom-component"></a>Utworzenie wystąpienia składnika niestandardowego  
 Następnym krokiem jest można utworzyć wystąpienia niestandardowego składnika w formularzu. Ponieważ **przybornika** automatycznie kont dla nowego składnika jest równie proste jak tworzenie innych składnika lub kontrolki.  
  
#### <a name="to-create-an-instance-of-a-custom-component"></a>Aby utworzyć wystąpienie niestandardowych składników  
  
1.  Otwórz formularz projektu w **Projektant formularzy**.  
  
2.  W **przybornika**, kliknij kartę nowej nazwie **składniki ToolboxExample**.  
  
     Po kliknięciu karty zostanie wyświetlona **DemoComponent**.  
  
    > [!NOTE]
    >  Ze względu na wydajność, składników, w obszarze wypełniana automatycznie **przybornika** nie wyświetlaj niestandardowych map bitowych i <xref:System.Drawing.ToolboxBitmapAttribute> nie jest obsługiwane. Aby wyświetlić ikony dla niestandardowych składników w **przybornika**, użyj **wybierz elementy przybornika** okno dialogowe, aby załadować składnika.  
  
3.  Przeciągnij składnika na formularzu.  
  
     Wystąpienie składnika jest tworzony i dodawany do **zasobnik składnika**.  
  
## <a name="unloading-and-reloading-a-custom-component"></a>Zwolnienie i ponowne załadowanie niestandardowych składników  
 **Przybornika** uwzględnia składników w każdym ładowania projektu oraz gdy projekt jest zwolniony, powoduje usunięcie odwołania do projektu składników.  
  
#### <a name="to-experiment-with-the-effect-on-the-toolbox-of-unloading-and-reloading-components"></a>Eksperymentować wpływa na przybornika zwolnienie i ponowne załadowanie składników  
  
1.  Zwolnienie projektu z rozwiązania.  
  
     Aby uzyskać więcej informacji na temat zwalnianie projektów, zobacz [NIB: porady: zwolnienie i ponowne załadowanie projektów](http://msdn.microsoft.com/library/abc0155b-8fcb-4ffc-95b6-698518a7100b). Jeśli zostanie wyświetlony monit o zapisanie, wybierz **tak**.  
  
2.  Dodaj nową **aplikacji systemu Windows** projektu do rozwiązania. Otwórz formularz w **projektanta**.  
  
     **Składniki ToolboxExample** kartę z poprzednich projektu jest obecnie usunięty.  
  
3.  Załaduj ponownie `ToolboxExample` projektu.  
  
     **Składniki ToolboxExample** karcie teraz pojawi się.  
  
## <a name="next-steps"></a>Następne kroki  
 W tym przewodniku wykaże, że **przybornika** uwzględnia elementów projektu, ale **przybornika** jest również uwzględnia kontrolek. Wypróbuj Kontrolki niestandardowe przez dodawanie i usuwanie projektów kontroli z rozwiązania.  
  
## <a name="see-also"></a>Zobacz też  
 [Ogólne, Projektant formularzy systemu Windows, opcje — Okno dialogowe](http://msdn.microsoft.com/library/8dd170af-72f0-4212-b04b-034ceee92834)  
 [Porady: manipulowanie kart z przybornika](http://msdn.microsoft.com/library/21285050-cadd-455a-b1f5-a2289a89c4db)  
 [Wybierz elementy przybornika, okno dialogowe (Visual Studio)](http://msdn.microsoft.com/library/bd07835f-18a8-433e-bccc-7141f65263bb)  
 [Umieszczanie kontrolek na formularzach Windows Forms](../../../../docs/framework/winforms/controls/putting-controls-on-windows-forms.md)

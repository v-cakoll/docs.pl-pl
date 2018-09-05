---
title: 'Wskazówki: automatyczne zapełnianie Przybornika składnikami niestandardowymi'
ms.date: 03/30/2017
helpviewer_keywords:
- IToolboxService interface
- Toolbox [Windows Forms], populating
- custom components [Windows Forms], adding to Toolbox
ms.assetid: 2fa1e3e8-6b9f-42b2-97c0-2be57444dba4
ms.openlocfilehash: 488d51e748ea17b09e61b982db7abadc34f8e311
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43671894"
---
# <a name="walkthrough-automatically-populating-the-toolbox-with-custom-components"></a>Wskazówki: automatyczne zapełnianie Przybornika składnikami niestandardowymi
Jeśli składniki są zdefiniowane w projekcie w aktualnie otwarte rozwiązanie, zostanie automatycznie wyświetlona w **przybornika**, za pomocą trzeba wykonywać żadnych czynności przez użytkownika. Możesz również ręcznie wypełnić **przybornika** za pomocą składników niestandardowych za pomocą [wybierz przybornika dialogowego elementy (Visual Studio)](https://msdn.microsoft.com/library/bd07835f-18a8-433e-bccc-7141f65263bb), ale **przybornika** uwzględnia elementy w Twoim rozwiązaniu kompilacji danych wyjściowych o następującej charakterystyce:  
  
-   Implementuje <xref:System.ComponentModel.IComponent>;  
  
-   Nie ma <xref:System.ComponentModel.ToolboxItemAttribute> równa `false`;  
  
-   Nie ma <xref:System.ComponentModel.DesignTimeVisibleAttribute> równa `false`.  
  
> [!NOTE]
>  **Przybornika** nie jest zgodna z łańcuchów odwołania, dzięki czemu nie będą wyświetlane elementy, które nie są kompilowane przez projekt w rozwiązaniu.  
  
 W tym instruktażu pokazano, jak niestandardowy składnik jest automatycznie odzwierciedlana w **przybornika** Po skompilowaniu składnika. Zadania zilustrowane w tym przewodniku obejmują:  
  
-   Tworzenie projektu Windows Forms.  
  
-   Tworzenie niestandardowych składników.  
  
-   Tworzenie wystąpienia składnika niestandardowego.  
  
-   Zwalnianie i ponowne załadowanie niestandardowych składników.  
  
 Gdy to zrobisz, zostanie wyświetlony **przybornika** jest wypełniana przy użyciu składnika, który został utworzony.  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
## <a name="creating-the-project"></a>Tworzenie projektu  
 Pierwszym krokiem jest utworzenie projektu i konfigurowanie formularza.  
  
#### <a name="to-create-the-project"></a>Aby utworzyć projekt  
  
1.  Utwórz projekt aplikacji systemu Windows o nazwie `ToolboxExample` (**pliku** > **New** > **projektu**  >  **Visual C#** lub **języka Visual Basic** > **Classic Desktop** > **Windows Forms aplikacji**).  
  
2.  Dodaj nowy składnik do projektu. Wywołaj go `DemoComponent`.  
  
     Aby uzyskać więcej informacji, zobacz [NIB: instrukcje: dodawanie nowych elementów projektu](https://msdn.microsoft.com/library/63d3e16b-de6e-4bb5-a0e3-ecec762201ce).  
  
3.  Skompiluj projekt.  
  
4.  Z **narzędzia** menu, kliknij przycisk **opcje** elementu. Kliknij przycisk **ogólne** w obszarze **Windows Forms Designer** element i upewnij się, że **AutoToolboxPopulate** ustawiono opcję **True**.  
  
## <a name="creating-an-instance-of-a-custom-component"></a>Tworzenie wystąpienia składnika niestandardowego  
 Następnym krokiem jest do utworzenia wystąpienia składnika niestandardowego w formularzu. Ponieważ **przybornika** automatycznie kont dla nowego składnika, jest to tak proste, jak tworzenie innych składnika lub kontrolki.  
  
#### <a name="to-create-an-instance-of-a-custom-component"></a>Aby utworzyć wystąpienie składnika niestandardowego  
  
1.  Otwieranie formularza projektu w **projektanta formularzy**.  
  
2.  W **przybornika**, kliknij przycisk Nowa karta o nazwie **składniki ToolboxExample**.  
  
     Po kliknięciu karty, zostanie wyświetlony **DemoComponent**.  
  
    > [!NOTE]
    >  Ze względu na wydajność składników w obszarze automatycznie wypełniony **przybornika** niestandardowych map bitowych, nie są wyświetlane i <xref:System.Drawing.ToolboxBitmapAttribute> nie jest obsługiwane. Aby wyświetlić ikonę do składnika niestandardowego w **przybornika**, użyj **wybierz elementy przybornika** okno dialogowe, aby załadować składnika.  
  
3.  Przeciągnij składnik do formularza.  
  
     Wystąpienia składnika, zostanie utworzony i dodany do **zasobniku składnika**.  
  
## <a name="unloading-and-reloading-a-custom-component"></a>Zwalnianie i ponowne załadowanie niestandardowych składników  
 **Przybornika** uwzględnia składników w każdym ładowania projektu oraz gdy projekt jest zwalniana, powoduje usunięcie odwołania do składników projektów.  
  
#### <a name="to-experiment-with-the-effect-on-the-toolbox-of-unloading-and-reloading-components"></a>Aby eksperymentować z wpływu na przybornika zwalniania i ponownego ładowania składników  
  
1.  Zwolnij projekt z rozwiązania.  
  
     Aby uzyskać więcej informacji na temat zwalniając projekty, zobacz [NIB: instrukcje: zwolnienie i ponownego ładowania projektów](https://msdn.microsoft.com/library/abc0155b-8fcb-4ffc-95b6-698518a7100b). Jeśli zostanie wyświetlony monit, aby zapisać, wybierz opcję **tak**.  
  
2.  Dodaj nową **aplikacji Windows** projektu do rozwiązania. Otwórz formularz w **projektanta**.  
  
     **Składniki ToolboxExample** kartę z poprzednim projektu jest teraz usunięte.  
  
3.  Załaduj ponownie `ToolboxExample` projektu.  
  
     **Składniki ToolboxExample** karcie teraz będzie pojawiać się ponownie.  
  
## <a name="next-steps"></a>Następne kroki  
 Ten przewodnik pokazuje, że **przybornika** bierze pod uwagę elementów projektu, ale **przybornika** jest również uwzględnia kontrolki. Poeksperymentuj z Kontrolki niestandardowe, dodając i usuwając kontroli projektów w rozwiązaniu.  
  
## <a name="see-also"></a>Zobacz też  
 [Ogólne, Windows Forms Designer, okno dialogowe Opcje](https://msdn.microsoft.com/library/8dd170af-72f0-4212-b04b-034ceee92834)  
 [Porady: manipulowanie karty przybornika](https://msdn.microsoft.com/library/21285050-cadd-455a-b1f5-a2289a89c4db)  
 [Wybierz elementy przybornika, okno dialogowe (Visual Studio)](https://msdn.microsoft.com/library/bd07835f-18a8-433e-bccc-7141f65263bb)  
 [Umieszczanie kontrolek na formularzach Windows Forms](../../../../docs/framework/winforms/controls/putting-controls-on-windows-forms.md)

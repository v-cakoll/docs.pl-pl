---
title: 'Porady: Tworzenie formularza wzorzec szczegół za pomocą dwóch formantów DataRepeater (Visual Studio)'
ms.date: 07/20/2015
helpviewer_keywords:
- DataRepeater, master/detail tables
ms.assetid: eec43ae3-05d8-45a1-8d41-3803c6359dbe
ms.openlocfilehash: 84639a5d49a3fa4a8c6845793c39fc8a67c31e02
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33590910"
---
# <a name="how-to-create-a-masterdetail-form-by-using-two-datarepeater-controls-visual-studio"></a>Porady: tworzenie formularza wzorzec/szczegół za pomocą dwóch formantów DataRepeater (Visual Studio)
Powiązane dane można wyświetlić przy użyciu co najmniej dwóch <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> na tworzenie formularza wzorzec/szczegół formantów. Na przykład możesz wyświetlić listę klientów w jednym <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>i gdy użytkownik wybierze klienta, wyświetlona zostanie lista klienta na sekundę <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>.  
  
 Można wyświetlić dane dotyczące przez przeciąganie elementów szczegóły, które współużytkują tego samego węzła głównego tabeli z **źródeł danych** okna na <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> formantu. Na przykład, jeśli źródło danych tabeli klientów i powiązanej tabeli zamówienia, zostanie wyświetlony obu tabel jako węzły najwyższego poziomu w widoku drzewa w **źródeł danych** okna. Rozwiń węzeł klientów, dzięki czemu można zobaczyć kolumny. Zauważ, że ostatniej kolumny w liście jest rozwijane węzeł, który reprezentuje tabeli zamówienia. Ten węzeł reprezentuje powiązane zamówienia dla klienta.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-display-related-data-in-two-datarepeater-controls"></a>Aby wyświetlanie powiązanych danych w dwóch formantów DataRepeater  
  
1.  Przeciągnij dwa <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> formantów **Visual Basic PowerPacks** karcie **przybornika** formularza lub kontenera formantu.  
  
2.  Przeciągnij uchwyt zmiany rozmiaru i pozycji do określenia rozmiaru formantów i umieść je side-by-side.  
  
3.  Na **danych** menu, kliknij przycisk **Pokaż źródeł danych**.  
  
    > [!NOTE]
    >  Jeśli **źródeł danych** okna jest pusta, Dodaj źródło danych do niej. Aby uzyskać więcej informacji, zobacz [Dodawanie nowych źródeł danych](/visualstudio/data-tools/add-new-data-sources).  
  
4.  W **źródeł danych** okna, wybierz węzeł najwyższego poziomu głównego tabeli.  
  
5.  Zmień typ listy wzorcowej tabeli Szczegóły klikając **szczegóły** na liście rozwijanej na węźle tabeli.  
  
6.  Przeciągnij węzeł główny tabeli region szablonu elementu pierwszego <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> formantu.  
  
7.  Rozwiń węzeł główny tabeli, a następnie wybierz węzeł szczegółów powiązanej tabeli.  
  
8.  Zmień typ docelowej tabeli szczegółów szczegóły klikając **szczegóły** na liście rozwijanej na węźle tabeli.  
  
9. Wybierz ten węzeł tabeli i przeciągnij go na region szablonu elementu drugiego <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> formantu.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
 [Wprowadzenie do kontrolki DataRepeater](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)  
 [Instrukcje: wyświetlanie powiązanych danych w kontrolce DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)  
 [Porady: wyświetlanie powiązanych danych w systemie Windows formularzy aplikacji](/visualstudio/data-tools/bind-windows-forms-controls-to-data-in-visual-studio)  
 [Instrukcje: zmienianie wyglądu kontrolki DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)  
 [Rozwiązywanie problemów z kontrolką DataRepeater](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)

---
title: 'Porady: Tworzenie formularza wzorzec / szczegół za pomocą dwóch formantów DataRepeater (Visual Studio)'
ms.date: 07/20/2015
helpviewer_keywords:
- DataRepeater, master/detail tables
ms.assetid: eec43ae3-05d8-45a1-8d41-3803c6359dbe
ms.openlocfilehash: 84639a5d49a3fa4a8c6845793c39fc8a67c31e02
ms.sourcegitcommit: 70c76a12449439bac0f7a359866be5a0311ce960
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/25/2018
ms.locfileid: "39245543"
---
# <a name="how-to-create-a-masterdetail-form-by-using-two-datarepeater-controls-visual-studio"></a>Porady: tworzenie formularza wzorzec/szczegół za pomocą dwóch formantów DataRepeater (Visual Studio)
Powiązane dane można wyświetlić przy użyciu co najmniej dwóch <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> na tworzenie formularza wzorzec/szczegół formantów. Na przykład możesz chcieć wyświetlić listę klientów w jednej <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>i gdy użytkownik wybierze klienta, wyświetlić listę zamówień tego klienta w ciągu sekundy <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>.  
  
 Możesz wyświetlić dane dotyczące przez przeciąganie elementów szczegóły, które współużytkują ten sam węzeł główny tabeli, z **źródeł danych** okna na <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> kontroli. Na przykład, jeśli źródło danych tabeli Customers i powiązanej tabeli zamówienia, zostanie wyświetlony obie tabele jako węzły najwyższego poziomu w widoku drzewa w **źródeł danych** okna. Rozwiń węzeł klientów, dzięki czemu można zobaczyć kolumny. Należy zauważyć, że ostatnia kolumna na liście jest rozwijany węzeł, który reprezentuje tabeli zamówienia. Ten węzeł reprezentuje powiązane zamówienia dla klienta.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-display-related-data-in-two-datarepeater-controls"></a>Wyświetlanie powiązanych danych w dwóch formantów DataRepeater  
  
1.  Przeciągnij dwa <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> kontrolki z **Visual Basic PowerPacks** karcie **przybornika** formularza lub kontener formantu.  
  
2.  Przeciągnij uchwyty zmiany rozmiaru i położenia, rozmiaru kontrolki i ich położenie side-by-side.  
  
3.  Na **danych** menu, kliknij przycisk **Pokaż źródła danych**.  
  
    > [!NOTE]
    >  Jeśli **źródeł danych** okna jest pusta, Dodaj źródło danych do niego. Aby uzyskać więcej informacji, zobacz [dodasz nowe źródła danych](/visualstudio/data-tools/add-new-data-sources).  
  
4.  W **źródeł danych** okna, wybierz węzeł najwyższego poziomu dla głównej tabeli.  
  
5.  Zmień upuszczany typ tabeli głównej do szczegółów, klikając **szczegóły** w węźle tabeli na liście rozwijanej.  
  
6.  Przeciągnij węzeł główny tabeli na region szablonu elementu pierwszego <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> kontroli.  
  
7.  Rozwiń węzeł główny tabeli i wybierz węzeł szczegółów powiązanej tabeli.  
  
8.  Zmień upuszczany typ tabeli szczegółów do szczegółów, klikając **szczegóły** w węźle tabeli na liście rozwijanej.  
  
9. Wybierz węzeł w tej tabeli i przeciągnij go na region szablonu elementu drugiego <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> kontroli.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
 [Wprowadzenie do kontrolki DataRepeater](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)  
 [Instrukcje: wyświetlanie powiązanych danych w kontrolce DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)  
 [Porady: wyświetlanie powiązanych danych w Windows Forms aplikacji](/visualstudio/data-tools/bind-windows-forms-controls-to-data-in-visual-studio)  
 [Instrukcje: zmienianie wyglądu kontrolki DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)  
 [Rozwiązywanie problemów z kontrolką DataRepeater](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)

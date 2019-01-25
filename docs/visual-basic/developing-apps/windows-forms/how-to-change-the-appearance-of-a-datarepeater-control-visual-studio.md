---
title: 'Instrukcje: Zmienianie wyglądu formantu DataRepeater (Visual Studio)'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataRepeater, customizing
- DataRepeater, changing run time appearance
ms.assetid: 2af6dfce-760b-489e-b863-8da967f315c3
ms.openlocfilehash: e5508329ba716b53eff0c9e1bfe13e190fa1fd85
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54716638"
---
# <a name="how-to-change-the-appearance-of-a-datarepeater-control-visual-studio"></a>Instrukcje: Zmienianie wyglądu formantu DataRepeater (Visual Studio)
Możesz zmienić wygląd <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> formantu w czasie projektowania, ustawiając właściwości lub w czasie wykonywania, obsługując <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> zdarzeń.  
  
 Właściwości ustawione w czasie projektowania, po wybraniu sekcji szablon elementu kontrolka będzie należy powtórzyć dla każdego <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> w czasie wykonywania. Właściwości powiązane z wyglądem <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> kontrolkę będą widoczne w czasie wykonywania, pozostało tylko wtedy, gdy części kontenera odkryte (na przykład, jeśli <xref:System.Windows.Forms.Control.Padding%2A> ustawioną na wartość duże).  
  
 W czasie wykonywania właściwości dotyczące wygląd można ustawiona na podstawie warunków. Na przykład w przypadku planowania aplikacji możesz zmienić kolor tła elementu, aby ostrzec użytkowników, gdy element jest zaległa. W <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> programu obsługi zdarzeń, jeśli zostanie ustawiona właściwość w instrukcji warunkowej takie jak `If…Then`, musisz również użyć `Else` klauzulę, aby określić wygląd, gdy warunek nie jest spełniony.  
  
### <a name="to-change-the-appearance-at-design-time"></a>Aby zmienić wygląd w czasie projektowania  
  
1.  W programie Windows Forms Designer wybierz region szablonu (w prawym górnym) elementu <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> kontroli.  
  
2.  W oknie dialogowym właściwości wybierz właściwość, a następnie zmień wartość. Obejmują typowe właściwości, które wpływają na wygląd <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.BackgroundImage%2A>, <xref:System.Windows.Forms.Panel.BorderStyle%2A>, i <xref:System.Windows.Forms.Control.ForeColor%2A>.  
  
### <a name="to-change-the-appearance-at-run-time"></a>Aby zmienić wygląd w czasie wykonywania  
  
1.  W edytorze kodu, w przypadku menu rozwijanego, kliknij przycisk **drawitem —**.  
  
2.  W <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> procedura obsługi zdarzeń, Dodaj kod, aby ustawić właściwości:  
  
     [!code-csharp[VbPowerPacksDataRepeaterAppearance#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksDataRepeaterAppearance#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio_1.vb)]  
  
## <a name="example"></a>Przykład  
 Niektóre typowe dostosowania <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> kontroli obejmują wyświetlanie wierszy w naprzemiennych kolorów i zmieniając kolor pola na podstawie warunku. Poniższy przykład pokazuje, jak wykonywać te dostosowania. W tym przykładzie przyjęto założenie, iż <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> formant, który jest powiązany z tabeli Produkty w bazie danych Northwind.  
  
 [!code-vb[VbPowerPacksDataRepeaterAlternateBackColor#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio_2.vb)]
 [!code-csharp[VbPowerPacksDataRepeaterAlternateBackColor#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio_2.cs)]  
  
 Należy pamiętać, że oba te dostosowania należy podać kod, aby ustawić właściwości dla obu stron warunku. Jeśli nie określisz `Else` warunek, zostanie wyświetlony nieoczekiwane wyniki w czasie wykonywania.  
  
## <a name="see-also"></a>Zobacz także
- <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>
- <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem>
- [Wprowadzenie do kontrolki DataRepeater](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)
- [Rozwiązywanie problemów z kontrolką DataRepeater](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
- [Instrukcje: Wyświetlanie powiązanych danych w formancie DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)
- [Instrukcje: Wyświetlanie formantów niepowiązanych w formancie DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md)
- [Instrukcje: Wyświetlanie nagłówków elementów w formancie DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-item-headers-in-a-datarepeater-control-visual-studio.md)

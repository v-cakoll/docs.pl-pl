---
title: 'Porady: zmienianie wyglądu formantu DataRepeater (Visual Studio)'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataRepeater, customizing
- DataRepeater, changing run time appearance
ms.assetid: 2af6dfce-760b-489e-b863-8da967f315c3
ms.openlocfilehash: 9863d9343ffcecc1e4aae7f6bc16dae39ef76385
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-change-the-appearance-of-a-datarepeater-control-visual-studio"></a>Porady: zmienianie wyglądu formantu DataRepeater (Visual Studio)
Można zmienić wygląd <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> formantu w czasie projektowania, ustawiając właściwości lub w czasie wykonywania Obsługa <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> zdarzeń.  
  
 Właściwości, które można ustawić w czasie projektowania, po wybraniu elementu sekcji szablonu formantu zostanie należy powtórzyć dla każdego <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> w czasie wykonywania. Właściwości związane z wygląd <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> kontrolki będą widoczne w czasie wykonywania, pozostało tylko wtedy, gdy w ramach kontenera niewykrytych (na przykład, jeśli <xref:System.Windows.Forms.Control.Padding%2A> właściwości jest ustawiona na wartość duże).  
  
 W czasie wykonywania powiązane z wyglądem właściwości można ustawiona na podstawie warunków. Na przykład w harmonogramie aplikacji, można zmienić kolor tła elementu, aby ostrzec użytkowników, gdy element jest zaległa. W <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> program obsługi zdarzeń, jeśli zostanie ustawiona właściwość w instrukcji warunkowej takich jak `If…Then`, należy również użyć `Else` klauzuli, aby określić wygląd, jeśli nie jest spełniony warunek.  
  
### <a name="to-change-the-appearance-at-design-time"></a>Zmiana wyglądu w czasie projektowania  
  
1.  W narzędziu Projektant dla formularzy systemu Windows wybierz region szablonu (wielkich) elementu <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> formantu.  
  
2.  W oknie właściwości wybierz właściwość, a następnie zmień wartość. Wspólne właściwości, które mają wpływ na wygląd obejmują <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.BackgroundImage%2A>, <xref:System.Windows.Forms.Panel.BorderStyle%2A>, i <xref:System.Windows.Forms.Control.ForeColor%2A>.  
  
### <a name="to-change-the-appearance-at-run-time"></a>Zmiana wyglądu w czasie wykonywania  
  
1.  W edytorze kodu, w przypadku menu rozwijanego, kliknij przycisk **DrawItem**.  
  
2.  W <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> program obsługi zdarzeń, Dodaj kod, aby ustawić właściwości:  
  
     [!code-csharp[VbPowerPacksDataRepeaterAppearance#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksDataRepeaterAppearance#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio_1.vb)]  
  
## <a name="example"></a>Przykład  
 Niektóre typowe dostosowania <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> kontroli obejmują wyświetlanie wiersze w naprzemiennych kolorów i zmiana koloru pole na podstawie warunku. Poniższy przykład przedstawia sposób wykonywania tych dostosowań. W tym przykładzie przyjęto założenie, że masz <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> formant, który jest powiązany z tabeli Produkty bazy danych Northwind.  
  
 [!code-vb[VbPowerPacksDataRepeaterAlternateBackColor#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio_2.vb)]
 [!code-csharp[VbPowerPacksDataRepeaterAlternateBackColor#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio_2.cs)]  
  
 Należy pamiętać, że dla obu tych dostosowań, należy podać kod, aby ustawić właściwości po obu stronach warunku. Jeśli nie określisz `Else` warunku, zobaczysz nieoczekiwane wyniki w czasie wykonywania.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem>  
 [Wprowadzenie do kontrolki DataRepeater](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)  
 [Rozwiązywanie problemów z kontrolką DataRepeater](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)  
 [Instrukcje: wyświetlanie powiązanych danych w kontrolce DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)  
 [Instrukcje: wyświetlanie niepowiązanych kontrolek w kontrolce DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md)  
 [Instrukcje: wyświetlanie nagłówków elementów w kontrolce DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-item-headers-in-a-datarepeater-control-visual-studio.md)

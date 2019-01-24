---
title: 'Instrukcje: Wyszukiwanie danych w formancie DataRepeater (Visual Studio)'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataRepeater, implementing search
- DataRepeater, searching data
ms.assetid: a8ab5d17-b94f-43c4-8dd7-d0450226d73f
ms.openlocfilehash: 514e72afc9570071f57e385574456ff7d716bad7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54654389"
---
# <a name="how-to-search-data-in-a-datarepeater-control-visual-studio"></a>Instrukcje: Wyszukiwanie danych w formancie DataRepeater (Visual Studio)
Kiedy używasz <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> formant, który zawiera wiele rekordów, może zajść potrzeba Pozwalanie użytkownikom wyszukiwanie określonego rekordu. Zamiast wyszukiwanie danych w samej kontrolce, można zaimplementować wyszukiwania, badając bazowego <xref:System.Windows.Forms.BindingSource>. Jeśli element zostanie znaleziony, można użyć <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CurrentItemIndex%2A> właściwości zaznacz element i przewiń ją do widoku.  
  
### <a name="to-implement-search"></a>Aby zaimplementować wyszukiwania  
  
1.  Przeciągnij <xref:System.Windows.Forms.TextBox> z kontrolować **przybornika** na formularz, który zawiera <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> kontroli.  
  
2.  W oknie Właściwości zmień **nazwa** właściwości **SearchTextBox**.  
  
3.  Przeciągnij <xref:System.Windows.Forms.Button> z kontrolować **przybornika** na formularz, który zawiera <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> kontroli.  
  
4.  W oknie Właściwości zmień **nazwa** właściwości **SearchButton**. Zmiana **tekstu** właściwości **wyszukiwania**.  
  
5.  Kliknij dwukrotnie <xref:System.Windows.Forms.Button> sterowania, aby otworzyć Edytor kodu i Dodaj następujący kod do `SearchButton_Click` programu obsługi zdarzeń.  
  
     [!code-vb[VbPowerPacksDataRepeaterSearch#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-search-data-in-a-datarepeater-control-visual-studio_1.vb)]
     [!code-csharp[VbPowerPacksDataRepeaterSearch#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-search-data-in-a-datarepeater-control-visual-studio_1.cs)]  
  
     Zastąp *ProductsBindingSource* o nazwie <xref:System.Windows.Forms.BindingSource> dla Twojego <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>i Zastąp *ProductID* o nazwie pola, które chcesz przeszukać.  
  
## <a name="see-also"></a>Zobacz także
- <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>
- [Wprowadzenie do kontrolki DataRepeater](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)
- [Rozwiązywanie problemów z kontrolką DataRepeater](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
- [Instrukcje: Zmienianie wyglądu formantu DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)

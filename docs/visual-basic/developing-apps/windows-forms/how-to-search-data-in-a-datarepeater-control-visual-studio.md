---
title: 'Porady: wyszukiwanie danych w formancie DataRepeater (Visual Studio)'
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataRepeater, implementing search
- DataRepeater, searching data
ms.assetid: a8ab5d17-b94f-43c4-8dd7-d0450226d73f
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a3ed7138c142a83584ecd19ccaebe0e31e421ce3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-search-data-in-a-datarepeater-control-visual-studio"></a>Porady: wyszukiwanie danych w formancie DataRepeater (Visual Studio)
W przypadku używania <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> kontrolkę, która zawiera dużą liczbę rekordów, może zajść potrzeba Pozwalanie użytkownikom wyszukiwanie określonego rekordu. Zamiast wyszukiwanie danych w formancie, można zaimplementować wyszukiwania, badając odpowiadającego <xref:System.Windows.Forms.BindingSource>. Jeśli element zostanie znaleziony, można użyć <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CurrentItemIndex%2A> właściwości zaznacz element i przewiń go do widoku.  
  
### <a name="to-implement-search"></a>Aby zaimplementować wyszukiwania  
  
1.  Przeciągnij <xref:System.Windows.Forms.TextBox> kontrolować z **przybornika** na formularz, który zawiera <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> formantu.  
  
2.  W oknie Właściwości zmień **nazwa** właściwości **SearchTextBox**.  
  
3.  Przeciągnij <xref:System.Windows.Forms.Button> kontrolować z **przybornika** na formularz, który zawiera <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> formantu.  
  
4.  W oknie Właściwości zmień **nazwa** właściwości **SearchButton**. Zmień **tekst** właściwości **wyszukiwania**.  
  
5.  Kliknij dwukrotnie <xref:System.Windows.Forms.Button> sterowania, aby otworzyć edytora kodu i Dodaj następujący kod do `SearchButton_Click` obsługi zdarzeń.  
  
     [!code-vb[VbPowerPacksDataRepeaterSearch#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-search-data-in-a-datarepeater-control-visual-studio_1.vb)]
     [!code-csharp[VbPowerPacksDataRepeaterSearch#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-search-data-in-a-datarepeater-control-visual-studio_1.cs)]  
  
     Zastąp *ProductsBindingSource* o nazwie <xref:System.Windows.Forms.BindingSource> dla Twojego <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>i Zastąp *ProductID* nazwą pola, które chcesz wyszukać.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
 [Wprowadzenie do formantu DataRepeater](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)  
 [Rozwiązywanie problemów z formantem DataRepeater](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)  
 [Porady: Zmienianie wyglądu formantu DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)

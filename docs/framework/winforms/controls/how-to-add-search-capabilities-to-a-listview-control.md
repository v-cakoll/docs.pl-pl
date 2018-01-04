---
title: 'Porady: dodawanie funkcji wyszukiwania do formantu ListView'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- lists [Windows Forms], enabling searching
- list views [Windows Forms], enabling searching
- ListView control [Windows Forms], adding search capabilities
- searching [Windows Forms], adding search capabilities to ListView control
ms.assetid: 557782d9-b705-4bab-b496-9938afddac82
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 111fc6e4945998c99e63560afab6104f4daf89e8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-search-capabilities-to-a-listview-control"></a>Porady: dodawanie funkcji wyszukiwania do formantu ListView
Często podczas pracy z dużą listę elementów w <xref:System.Windows.Forms.ListView> kontroli, które chcesz zaoferować możliwości wyszukiwania dla użytkownika. <xref:System.Windows.Forms.ListView> Formant oferuje tę możliwość na dwa sposoby: dopasowywania tekstu i lokalizację wyszukiwania.  
  
 <xref:System.Windows.Forms.ListView.FindItemWithText%2A> Metoda służy do wyszukiwania tekstu w <xref:System.Windows.Forms.ListView> w widoku listy lub szczegółów podany ciąg wyszukiwania i opcjonalnie początkową i końcową indeksu. Z kolei <xref:System.Windows.Forms.ListView.FindNearestItem%2A> metoda pozwala znaleźć element <xref:System.Windows.Forms.ListView> w widoku ikon lub kafelka, mając do dyspozycji zestaw współrzędne x i y i kierunek do wyszukiwania.  
  
### <a name="to-find-an-item-using-text"></a>Aby znaleźć element przy użyciu tekstu  
  
1.  Utwórz <xref:System.Windows.Forms.ListView> z <xref:System.Windows.Forms.ListView.View%2A> ustawioną właściwość <xref:System.Windows.Forms.View.Details> lub <xref:System.Windows.Forms.View.List>, a następnie wypełnij <xref:System.Windows.Forms.ListView> z elementami.  
  
2.  Wywołanie <xref:System.Windows.Forms.ListView.FindItemWithText%2A> jest metoda tekst elementu, który chcesz odnaleźć.  
  
3.  Poniższy przykładowy kod przedstawia sposób tworzenia prostej <xref:System.Windows.Forms.ListView>umieścić w nim elementów i użyj wprowadzanie tekstu od użytkownika, aby znaleźć element na liście.  
  
 [!code-cpp[System.Windows.Forms.ListViewFindItems#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/cpp/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.ListViewFindItems#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.ListViewFindItems#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/VB/form1.vb#1)]  
  
### <a name="to-find-an-item-using-x--and-y-coordinates"></a>Aby znaleźć element za pomocą współrzędnych x i y  
  
1.  Utwórz <xref:System.Windows.Forms.ListView> z <xref:System.Windows.Forms.View> ustawioną właściwość <xref:System.Windows.Forms.View.SmallIcon> lub <xref:System.Windows.Forms.View.LargeIcon>, a następnie wypełnij <xref:System.Windows.Forms.ListView> z elementami.  
  
2.  Wywołanie <xref:System.Windows.Forms.ListView.FindNearestItem%2A> jest metoda żądaną współrzędne x i y- a kierunek chcesz wyszukać.  
  
3.  Poniższy przykładowy kod przedstawia sposób tworzenia podstawowych ikona <xref:System.Windows.Forms.ListView>, umieścić w nim elementów i przechwytywania <xref:System.Windows.Forms.Control.MouseDown> zdarzenia do znalezienia najbliższej element w górę kierunku.  
  
 [!code-cpp[System.Windows.Forms.ListViewFindItems#2](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/cpp/form1.cpp#2)]
 [!code-csharp[System.Windows.Forms.ListViewFindItems#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/CS/form1.cs#2)]
 [!code-vb[System.Windows.Forms.ListViewFindItems#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/VB/form1.vb#2)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.ListView>  
 <xref:System.Windows.Forms.ListView.FindItemWithText%2A>  
 <xref:System.Windows.Forms.ListView.FindNearestItem%2A>  
 [Kontrolka ListView](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)  
 [ListView, kontrolka — omówienie](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)  
 [Instrukcje: dodawanie i usuwanie elementów za pomocą kontrolki ListView formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)

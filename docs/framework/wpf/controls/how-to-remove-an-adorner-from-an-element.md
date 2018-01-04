---
title: "Jak usunąć moduł definiowania układów z elementu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: adorners [WPF], removing
ms.assetid: 97cf4d9f-0596-429e-8526-32a30aa4ae99
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 20d17ef43f99f6815334c0acbf7eb2040959751e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-remove-an-adorner-from-an-element"></a>Jak usunąć moduł definiowania układów z elementu
W tym przykładzie pokazano, jak programowane usuwanie określonego modułu definiowania układu kodu z określonej <xref:System.Windows.UIElement>.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie kodu usuwa pierwszego modułu definiowania układu kodu w tablicy definiowania układu zwrócony przez <xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A>.  W tym przykładzie stanie się pobrać modułu definiowania układu kodu na <xref:System.Windows.UIElement> o nazwie *myTextBox*.  Jeśli element określony w wywołaniu <xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A> nie ma takich modułów, `null` jest zwracany.  Ten kod jawnie sprawdza tablicy o wartości null i jest najbardziej odpowiednie dla aplikacji, gdzie powinien być stosunkowo wspólnej tablicy o wartości null.  
  
 [!code-csharp[AdornersMiscCode#_RemoveSpecificAdornerLong](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdornersMiscCode/CSharp/Window1.xaml.cs#_removespecificadornerlong)]
 [!code-vb[AdornersMiscCode#_RemoveSpecificAdornerLong](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdornersMiscCode/visualbasic/window1.xaml.vb#_removespecificadornerlong)]  
  
## <a name="example"></a>Przykład  
 W tym przykładzie kodu skrócone jest funkcjonalnym odpowiednikiem pełne przykładzie przedstawionym powyżej. Ten kod nie sprawdza jawnie dla tablicy o wartości null, więc istnieje możliwość, że <xref:System.NullReferenceException> może zostać zgłoszony wyjątek.  Ten kod jest najbardziej odpowiednie dla aplikacji, gdzie powinien być rzadko tablicy o wartości null.  
  
 [!code-csharp[AdornersMiscCode#_RemoveSpecificAdornerShort](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdornersMiscCode/CSharp/Window1.xaml.cs#_removespecificadornershort)]
 [!code-vb[AdornersMiscCode#_RemoveSpecificAdornerShort](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdornersMiscCode/visualbasic/window1.xaml.vb#_removespecificadornershort)]  
  
## <a name="see-also"></a>Zobacz też  
 [Moduły indeksowania układu — omówienie](../../../../docs/framework/wpf/controls/adorners-overview.md)

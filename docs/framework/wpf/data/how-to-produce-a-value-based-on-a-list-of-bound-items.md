---
title: "Jak uzyskać wartość w oparciu o listę powiązanych elementów"
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
helpviewer_keywords:
- data binding [WPF], MultiBinding
- Multibinding [WPF]
ms.assetid: b3d06378-b511-4181-95aa-316d60c9229b
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7d16a198ed78c1ffd9dcaad595e9cc9be3cb2de0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-produce-a-value-based-on-a-list-of-bound-items"></a>Jak uzyskać wartość w oparciu o listę powiązanych elementów
<xref:System.Windows.Data.MultiBinding>Umożliwia powiązać właściwość target powiązanie listę właściwości źródła, a następnie zastosować logiki w celu utworzenia wartości o dane wejściowe. W tym przykładzie przedstawiono sposób użycia <xref:System.Windows.Data.MultiBinding>.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie `NameListData` odwołuje się do kolekcji `PersonName` obiektów, które są obiekty, które zawierają dwie właściwości, `firstName` i `lastName`. Poniższy przykład tworzy <xref:System.Windows.Controls.TextBlock> który pokazuje imiona i nazwiska osoby z nazwisko pierwszy.  
  
 [!code-xaml[MultiBinding#Resources1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#resources1)]  
[!code-xaml[MultiBinding#Resources2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#resources2)]  
[!code-xaml[MultiBinding#MultiBindingTextBox2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#multibindingtextbox2)]  
[!code-xaml[MultiBinding#Window](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#window)]  
  
 Aby zrozumieć, jak jest generowany format ostatnich nazwę pierwszego, Spójrzmy na implementacji `NameConverter`:  
  
 [!code-csharp[MultiBinding#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/NameConverter.cs#3)]
 [!code-vb[MultiBinding#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MultiBinding/VisualBasic/NameConverter.vb#3)]  
  
 `NameConverter`implementuje <xref:System.Windows.Data.IMultiValueConverter> interfejsu. `NameConverter`pobiera wartości poszczególnych powiązania i przechowuje je w tablicy wartości obiektu. Kolejność <xref:System.Windows.Data.Binding> elementy są wyświetlane w obszarze <xref:System.Windows.Data.MultiBinding> element to kolejność, w jakiej te wartości są przechowywane w tablicy. Wartość <xref:System.Windows.Data.MultiBinding.ConverterParameter%2A> odwołuje się atrybut argument parametru <xref:System.Windows.Data.MultiBinding.Converter%2A> metodę, która wykonuje przełącznik na parametr, aby określić, w jaki format nazwy.  
  
## <a name="see-also"></a>Zobacz też  
 [Konwertuj powiązana z danymi](../../../../docs/framework/wpf/data/how-to-convert-bound-data.md)  
 [Omówienie powiązania danych](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Tematy porad](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)

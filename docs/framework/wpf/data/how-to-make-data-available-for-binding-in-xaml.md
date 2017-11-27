---
title: "Jak udostępnić dane do powiązania w XAML"
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
- data binding [WPF], making data available for binding
- binding data [WPF], making data available for
ms.assetid: 7103c2e8-0e31-4a13-bf12-ca382221a8d5
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d734a7f17f8843ff284ac0854ac41d4a5b9f5584
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-make-data-available-for-binding-in-xaml"></a>Jak udostępnić dane do powiązania w XAML
W tym temacie opisano różne sposoby, które można udostępnić dane dla powiązania w [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]w zależności od potrzeb aplikacji.  
  
## <a name="example"></a>Przykład  
 Jeśli masz [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] obiektów, które chcesz powiązać z [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], jedną z metod można udostępnić obiekt do powiązania zdefiniować go jako zasób i nadaj mu `x:Key`. W poniższym przykładzie należy `Person` obiektu z właściwością ciągu o nazwie `PersonName`. `Person` Obiektu jest zdefiniowana w obszarze nazw o nazwie `SDKSample`.  
  
 [!code-xaml[SimpleBinding#Instantiation](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml#instantiation)]  
[!code-xaml[SimpleBinding#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml#2)]  
  
 Następnie możesz powiązać do obiektu w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], jak pokazano w poniższym przykładzie.  
  
 [!code-xaml[SimpleBinding#BDO1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml#bdo1)]  
  
 Alternatywnie można użyć <xref:System.Windows.Data.ObjectDataProvider> klasy, jak w poniższym przykładzie.  
  
 [!code-xaml[SimpleBinding#ODPCP](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Page1.xaml#odpcp)]  
  
 Zdefiniuj powiązania taki sam sposób:  
  
 [!code-xaml[SimpleBinding#BDO1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml#bdo1)]  
  
 W tym przykładzie, wynikiem jest taki sam: masz <xref:System.Windows.Controls.TextBlock> z zawartości tekstowej `Joe`. Jednak <xref:System.Windows.Data.ObjectDataProvider> klasa udostępnia funkcje, takie jak możliwość powiązać wynik metody. Możesz użyć <xref:System.Windows.Data.ObjectDataProvider> klasy, jeśli potrzebujesz funkcji zapewnia.  
  
 Jednak są wiązane obiekt, który został już utworzony, należy ustawić `DataContext` w kodzie, jak w poniższym przykładzie.  
  
 [!code-csharp[ADODataSet#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml.cs#1)]
 [!code-vb[ADODataSet#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ADODataSet/VisualBasic/Window1.xaml.vb#1)]  
  
 Aby uzyskać dostęp do [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] dane dotyczące korzystania z wiązania <xref:System.Windows.Data.XmlDataProvider> , zobacz [powiązania danych XML przy użyciu XMLDataProvider i kwerendy XPath](../../../../docs/framework/wpf/data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md). Aby uzyskać dostęp do [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] dane dotyczące korzystania z wiązania <xref:System.Windows.Data.ObjectDataProvider> , zobacz [powiązanie klasy XDocument, klasy XElement lub LINQ dla wyników zapytania XML](../../../../docs/framework/wpf/data/how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md).  
  
 Informacje o różnych sposobach można określić dokonywane jest wiązanie danych, zobacz [określone źródło powiązania](../../../../docs/framework/wpf/data/how-to-specify-the-binding-source.md). Informacje o jakie typy danych można powiązać i sposobu wdrażania własnych [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] obiektów dla powiązania, zobacz [omówienie źródeł powiązania](../../../../docs/framework/wpf/data/binding-sources-overview.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Omówienie powiązania danych](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Tematy porad](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)

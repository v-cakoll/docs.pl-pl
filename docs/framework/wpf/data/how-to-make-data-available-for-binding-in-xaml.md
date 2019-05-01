---
title: 'Instrukcje: Udostępnianie danych do powiązania w XAML'
ms.date: 01/29/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], making data available for binding
- binding data [WPF], making data available for
ms.assetid: 7103c2e8-0e31-4a13-bf12-ca382221a8d5
ms.openlocfilehash: 2d51f06da31482c46b04d1eb86172c3eda246c20
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62010309"
---
# <a name="how-to-make-data-available-for-binding-in-xaml"></a>Instrukcje: Udostępnianie danych do powiązania w XAML
W tym temacie omówiono różne sposoby, które można udostępnić dane do powiązania w [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], w zależności od potrzeb aplikacji.  
  
## <a name="example"></a>Przykład  
 Jeśli masz [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] obiektów, które chcesz powiązać z [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], jeden ze sposobów, które można udostępnić obiektu dla powiązania jest do definiowania go jako zasób i nadaj mu `x:Key`. W poniższym przykładzie użytkownik ma `Person` obiektu z właściwością ciągu o nazwie `PersonName`. `Person` Obiektu (w wierszu wyświetlane wyróżnione zawierający `<src>` elementu) jest zdefiniowany w przestrzeni nazw o nazwie `SDKSample`.  
  
 [!code-xaml[SimpleBinding#Instantiation](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml?highlight=9,37)]  
  
 Następnie możesz powiązać <xref:System.Windows.Controls.TextBlock> formantu do obiektu w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], jak wyróżniony wiersz zawiera `<TextBlock>` pokazuje element. 
  
 Alternatywnie, można użyć <xref:System.Windows.Data.ObjectDataProvider> klasy, jak w poniższym przykładzie:  
  
 [!code-xaml[ObjectDataProvider}](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Page1.xaml?highlight=10-14,42)]  
  
 Zdefiniuj powiązanie taki sam sposób, jak wyróżniony wiersz, który zawiera `<TextBlock>` pokazuje element.  
  
 W tym przykładzie, wynik jest taki sam: masz <xref:System.Windows.Controls.TextBlock> z zawartością tekstową `Joe`. Jednak <xref:System.Windows.Data.ObjectDataProvider> klasa oferuje funkcje, takie jak możliwość powiązania do wyniku metody. Możesz użyć <xref:System.Windows.Data.ObjectDataProvider> klasy, jeśli potrzebujesz funkcji zapewnia.  
  
 Jednak jeśli dokonywane jest wiązanie obiektu, który został już utworzony, musisz ustawić `DataContext` w kodzie, jak w poniższym przykładzie.  
  
 [!code-csharp[ADODataSet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml.cs#1)]
 [!code-vb[ADODataSet#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ADODataSet/VisualBasic/Window1.xaml.vb#1)]  
  
 Aby uzyskać dostęp do [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] dane dotyczące korzystania z wiązania <xref:System.Windows.Data.XmlDataProvider> klasy, zobacz [powiązania danych XML przy użyciu XMLDataProvider i zapytań XPath](how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md). Aby uzyskać dostęp do [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] dane dotyczące korzystania z wiązania <xref:System.Windows.Data.ObjectDataProvider> klasy, zobacz [Powiąż z dokumentem, elementem x lub LINQ dla wyników zapytań XML](how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md).  
  
 Aby uzyskać informacje o wiele sposobów, można określić dane, w której dokonywane jest wiązanie, zobacz [określić źródło wiążące](how-to-specify-the-binding-source.md). Więcej informacji o jakie typy danych można powiązać i jak implementować własne [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] obiektów dla powiązania, zobacz [wiązanie źródeł — omówienie](binding-sources-overview.md).  
  
## <a name="see-also"></a>Zobacz także

- [Powiązanie danych — omówienie](data-binding-overview.md)
- [Tematy z instrukcjami](data-binding-how-to-topics.md)

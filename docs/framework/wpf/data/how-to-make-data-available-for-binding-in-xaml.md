---
title: Jak udostępnić dane do powiązania w XAML
ms.date: 01/29/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], making data available for binding
- binding data [WPF], making data available for
ms.assetid: 7103c2e8-0e31-4a13-bf12-ca382221a8d5
ms.openlocfilehash: 91e89dbf36024c31f4afcd9b6d956944baf13576
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174189"
---
# <a name="how-to-make-data-available-for-binding-in-xaml"></a>Jak udostępnić dane do powiązania w XAML
W tym temacie omówiono różne sposoby [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]udostępniania danych do powiązania w programie , w zależności od potrzeb aplikacji.  
  
## <a name="example"></a>Przykład  
 Jeśli masz wspólny obiekt środowiska uruchomieniowego języka (CLR), [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]z którego chcesz powiązać, jednym ze sposobów udostępnienia obiektu `x:Key`do powiązania jest zdefiniowanie go jako zasobu i nadanie mu . W poniższym przykładzie `Person` masz obiekt o `PersonName`nazwie . Obiekt `Person` (w wyświetlonym wierszu wyróżnionym, `<src>` który zawiera element) `SDKSample`jest zdefiniowany w obszarze nazw o nazwie .  
  
 [!code-xaml[SimpleBinding#Instantiation](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml?highlight=9,37)]  
  
 Następnie można powiązać <xref:System.Windows.Controls.TextBlock> formant [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]z obiektem w , `<TextBlock>` jak podświetlony wiersz, który zawiera element.
  
 Alternatywnie można użyć <xref:System.Windows.Data.ObjectDataProvider> klasy, jak w poniższym przykładzie:  
  
 [!code-xaml[ObjectDataProvider}](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Page1.xaml?highlight=10-14,42)]  
  
 Wiązania można zdefiniować w taki sam sposób, `<TextBlock>` jak wyróżniony wiersz, który zawiera element pokazuje.  
  
 W tym konkretnym przykładzie wynik jest <xref:System.Windows.Controls.TextBlock> taki sam: `Joe`masz z zawartością tekstową . Jednak <xref:System.Windows.Data.ObjectDataProvider> klasa zapewnia funkcje, takie jak możliwość powiązania z wynikiem metody. Można użyć klasy, <xref:System.Windows.Data.ObjectDataProvider> jeśli potrzebujesz funkcji, które zapewnia.  
  
 Jednak jeśli są wiążące dla obiektu, który został już `DataContext` utworzony, należy ustawić w kodzie, jak w poniższym przykładzie.  
  
 [!code-csharp[ADODataSet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml.cs#1)]
 [!code-vb[ADODataSet#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ADODataSet/VisualBasic/Window1.xaml.vb#1)]  
  
 Aby uzyskać dostęp do danych <xref:System.Windows.Data.XmlDataProvider> XML do powiązania przy użyciu klasy, zobacz [Powiązanie danych XML przy użyciu aplikacji XMLDataProvider i XPath Queries](how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md). Aby uzyskać dostęp do danych <xref:System.Windows.Data.ObjectDataProvider> XML do powiązania przy użyciu klasy, zobacz [Bind to XDocument, XElement lub LINQ for XML Query Results](how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md).  
  
 Aby uzyskać informacje o wielu sposobach określania danych, z których użytkownik jest powiązany, zobacz [Określanie źródła wiązania](how-to-specify-the-binding-source.md). Aby uzyskać informacje o typach danych, z jakimi można powiązać lub jak zaimplementować własne obiekty środowiska wykonawczego języka wspólnego (CLR) do wiązania, zobacz [Omówienie źródeł powiązania.](binding-sources-overview.md)  
  
## <a name="see-also"></a>Zobacz też

- [Przegląd Wiązanie danych](../../../desktop-wpf/data/data-binding-overview.md)
- [Tematy in jakże](data-binding-how-to-topics.md)

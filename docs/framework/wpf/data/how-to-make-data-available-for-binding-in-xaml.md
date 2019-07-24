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
ms.openlocfilehash: 3487a160cc49ab6b779a20157668915c2da33900
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2019
ms.locfileid: "68401491"
---
# <a name="how-to-make-data-available-for-binding-in-xaml"></a>Instrukcje: Udostępnianie danych do powiązania w XAML
W tym temacie omówiono różne sposoby tworzenia danych do powiązania w programie, [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]w zależności od potrzeb aplikacji.  
  
## <a name="example"></a>Przykład  
 Jeśli masz obiekt środowiska uruchomieniowego języka wspólnego (CLR), z którym chcesz utworzyć powiązanie, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]jednym ze sposobów, aby można było uzyskać dostęp do obiektu dla powiązania, jest definiowanie go jako zasobu i nadanie `x:Key`mu. W poniższym przykładzie masz `Person` obiekt z właściwością ciągu o nazwie. `PersonName` Obiekt (w wyświetlonym wierszu wyróżniony, który `<src>` zawiera element) jest zdefiniowany w przestrzeni nazw o `SDKSample`nazwie. `Person`  
  
 [!code-xaml[SimpleBinding#Instantiation](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml?highlight=9,37)]  
  
 Następnie można powiązać <xref:System.Windows.Controls.TextBlock> formant z obiektem w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], jako `<TextBlock>` wyróżniony wiersz, który zawiera element. 
  
 Alternatywnie można użyć <xref:System.Windows.Data.ObjectDataProvider> klasy, jak w poniższym przykładzie:  
  
 [!code-xaml[ObjectDataProvider}](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Page1.xaml?highlight=10-14,42)]  
  
 Powiązanie można zdefiniować w taki sam sposób, jak wyróżniony wiersz zawierający `<TextBlock>` element.  
  
 W tym konkretnym przykładzie wynik jest taki sam, jak <xref:System.Windows.Controls.TextBlock> w przypadku zawartości `Joe`tekstowej. <xref:System.Windows.Data.ObjectDataProvider> Jednak Klasa zawiera funkcje, takie jak możliwość powiązania z wynikami metody. Możesz wybrać użycie klasy, <xref:System.Windows.Data.ObjectDataProvider> Jeśli potrzebujesz jej funkcjonalności.  
  
 Jeśli jednak tworzysz powiązanie z obiektem, który został już utworzony, musisz ustawić `DataContext` kod w kodzie, jak w poniższym przykładzie.  
  
 [!code-csharp[ADODataSet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml.cs#1)]
 [!code-vb[ADODataSet#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ADODataSet/VisualBasic/Window1.xaml.vb#1)]  
  
 Aby uzyskać [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] dostęp do danych dla powiązania <xref:System.Windows.Data.XmlDataProvider> przy użyciu klasy, zobacz [Powiązywanie z danymi XML przy użyciu XmlDataProvider i zapytań XPath](how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md). Aby uzyskać [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] dostęp do danych dla powiązania <xref:System.Windows.Data.ObjectDataProvider> przy użyciu klasy, zobacz [bind to XDocuments, XElement lub LINQ for XML Results](how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md).  
  
 Aby uzyskać informacje o wielu sposobach określania danych, do których są wiązane, zobacz [Określanie źródła powiązania](how-to-specify-the-binding-source.md). Aby uzyskać informacje o typach danych, z którymi można powiązać lub jak zaimplementować własne obiekty środowiska uruchomieniowego języka wspólnego (CLR) na potrzeby tworzenia powiązań, zobacz [Omówienie źródeł powiązań](binding-sources-overview.md).  
  
## <a name="see-also"></a>Zobacz także

- [Powiązanie danych — omówienie](data-binding-overview.md)
- [Tematy z instrukcjami](data-binding-how-to-topics.md)

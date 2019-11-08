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
ms.openlocfilehash: 97e878e4932ca9122bf27f76c32d1a56e69f253a
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2019
ms.locfileid: "73740605"
---
# <a name="how-to-make-data-available-for-binding-in-xaml"></a>Jak udostępnić dane do powiązania w XAML
W tym temacie omówiono różne sposoby udostępniania danych do powiązań w [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], w zależności od potrzeb aplikacji.  
  
## <a name="example"></a>Przykład  
 Jeśli masz obiekt środowiska uruchomieniowego języka wspólnego (CLR), z którym chcesz utworzyć powiązanie z [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], jednym ze sposobów udostępnienia obiektu do powiązania jest zdefiniowanie go jako zasobu i nadanie mu `x:Key`. W poniższym przykładzie masz `Person` obiekt z właściwością ciągu o nazwie `PersonName`. Obiekt `Person` (w wyróżnionym wierszu zawierającym element `<src>`) jest zdefiniowany w przestrzeni nazw o nazwie `SDKSample`.  
  
 [!code-xaml[SimpleBinding#Instantiation](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml?highlight=9,37)]  
  
 Następnie można powiązać formant <xref:System.Windows.Controls.TextBlock> z obiektem w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], jak wyróżniony wiersz zawiera element `<TextBlock>`. 
  
 Alternatywnie można użyć klasy <xref:System.Windows.Data.ObjectDataProvider>, jak w poniższym przykładzie:  
  
 [!code-xaml[ObjectDataProvider}](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Page1.xaml?highlight=10-14,42)]  
  
 Powiązanie można zdefiniować w taki sam sposób, jak wyróżniony wiersz zawierający element `<TextBlock>`.  
  
 W tym konkretnym przykładzie wynik jest taki sam: masz <xref:System.Windows.Controls.TextBlock> z `Joe`zawartości tekstowej. Jednak Klasa <xref:System.Windows.Data.ObjectDataProvider> udostępnia funkcje, takie jak możliwość powiązania z wynikami metody. Możesz użyć klasy <xref:System.Windows.Data.ObjectDataProvider>, jeśli potrzebujesz jej funkcjonalności.  
  
 Jeśli jednak tworzysz powiązanie z obiektem, który został już utworzony, musisz ustawić `DataContext` w kodzie, jak w poniższym przykładzie.  
  
 [!code-csharp[ADODataSet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml.cs#1)]
 [!code-vb[ADODataSet#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ADODataSet/VisualBasic/Window1.xaml.vb#1)]  
  
 Aby uzyskać dostęp do danych XML dla powiązania przy użyciu klasy <xref:System.Windows.Data.XmlDataProvider>, zobacz [bind to XML Data przy użyciu XmlDataProvider i zapytań XPath](how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md). Aby uzyskać dostęp do danych XML dla powiązania przy użyciu klasy <xref:System.Windows.Data.ObjectDataProvider>, zobacz [bind to XDocuments, XElement lub LINQ for XML Results](how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md).  
  
 Aby uzyskać informacje o wielu sposobach określania danych, do których są wiązane, zobacz [Określanie źródła powiązania](how-to-specify-the-binding-source.md). Aby uzyskać informacje o typach danych, z którymi można powiązać lub jak zaimplementować własne obiekty środowiska uruchomieniowego języka wspólnego (CLR) na potrzeby tworzenia powiązań, zobacz [Omówienie źródeł powiązań](binding-sources-overview.md).  
  
## <a name="see-also"></a>Zobacz także

- [Powiązanie danych — omówienie](../../../desktop-wpf/data/data-binding-overview.md)
- [Tematy z instrukcjami](data-binding-how-to-topics.md)

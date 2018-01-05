---
title: "Jak użyć przestrzeni nazw XML w powiązaniu danych"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XML [WPF], namespaces
- data binding [WPF], XML namespaces
- namespaces [WPF], XML
ms.assetid: a47c832f-dc84-48f2-96d5-cde18fc4284b
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f23e041a1e6b283cfe5308d6aef861f1fc757a7d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-xml-namespaces-in-data-binding"></a>Jak użyć przestrzeni nazw XML w powiązaniu danych
## <a name="example"></a>Przykład  
 W tym przykładzie pokazano, jak obsługiwać określony w przestrzeni nazw Twojej [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] źródle powiązania.  
  
 Jeśli Twoje [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] dane mają następujące [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] definicję przestrzeni nazw:  
  
 `<rss version="2.0" xmlns:dc="http://purl.org/dc/elements/1.1/">`  
  
 Można użyć <xref:System.Windows.Data.XmlNamespaceMapping> element do mapowania do przestrzeni nazw <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A>, jak w poniższym przykładzie. Następnie można użyć <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A> do odwoływania się do [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] przestrzeni nazw. <xref:System.Windows.Controls.ListBox> w tym przykładzie wyświetlane są *tytuł* i *dc:date* każdego *elementu*.  
  
 [!code-xaml[XmlnsBindSnippet#XmlNamespaceMapping](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XmlnsBindSnippet/CS/Window1.xaml#xmlnamespacemapping)]  
  
 Należy pamiętać, że <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A> użytkownika nie ma zgodne z działaniem używanym w [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] źródła; w przypadku zmiany prefiks w [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] źródła mapowanie nadal działa.  
  
 W tym przykładzie [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] dane pochodzą z usługi sieci web, ale <xref:System.Windows.Data.XmlNamespaceMapping> element współdziała również z wbudowanym [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] lub [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] osadzonego pliku danych.  
  
## <a name="see-also"></a>Zobacz też  
 [Powiązywanie z danymi XML przy użyciu XMLDataProvider i zapytań XPath](../../../../docs/framework/wpf/data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)  
 [Powiązanie danych — omówienie](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Tematy z instrukcjami](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)

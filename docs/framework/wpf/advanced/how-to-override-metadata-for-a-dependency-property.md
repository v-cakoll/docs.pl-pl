---
title: "Jak zastąpić metadane dla właściwości zależności"
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
- metadata [WPF], overriding for dependency properties
- dependency properties [WPF], overriding metadata for
- overriding metadata for dependency properties [WPF]
ms.assetid: f90f026e-60d8-428a-933d-edf0dba4441f
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8e7cb01c81b5fb24830cbe0cc39befbadaf4405e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-override-metadata-for-a-dependency-property"></a>Jak zastąpić metadane dla właściwości zależności
W tym przykładzie pokazano, jak zastąpić domyślny metadanych właściwości zależności, które pochodzi z klasy dziedziczonej, wywołując <xref:System.Windows.DependencyProperty.OverrideMetadata%2A> — metoda i udostępnia metadane określonego typu.  
  
## <a name="example"></a>Przykład  
 Definiując jego <xref:System.Windows.PropertyMetadata>, klasy można zdefiniować właściwości zależności zachowania, takie jak jego domyślne wartości właściwości systemu wywołania zwrotne i. Wiele klas właściwość zależności jest już metadanych domyślne ustanowiony jako część procesu rejestracji. Dotyczy to również właściwości zależności, które są częścią [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)]. Klasa, która dziedziczy właściwości zależności za pomocą jego dziedziczenia klas można zastąpić oryginalnych metadanych tak, aby właściwości właściwości, które można zmienić za pomocą metadanych będzie odpowiadała żadnych wymagań specyficznych dla podklasy.  
  
 Zastępowanie metadanych dla właściwości zależności należy przeprowadzić przed tą właściwością zostanie umieszczona w użycia przez system właściwości (to jest równa godzinę, o której tworzone są określone wystąpienia obiektów, które rejestrują właściwości). Wywołuje się <xref:System.Windows.DependencyProperty.OverrideMetadata%2A> musi zostać wykonana konstruktorów statycznych typu, który udostępnia siebie jako `forType` parametr <xref:System.Windows.DependencyProperty.OverrideMetadata%2A>. Jeśli spróbujesz zmienić metadanych, gdy istnieje wystąpienie typu właściciela, to zostanie nie zgłaszaj wyjątków, ale spowoduje niespójność zachowania w systemie właściwości. Ponadto metadane tylko można zastąpić raz dla typu. Kolejne próby na zastępowanie metadanych do tego samego typu zgłosi wyjątek.  
  
 W poniższym przykładzie, niestandardowe klasy `MyAdvancedStateControl` zastępuje metadane podane dla `StateProperty` przez `MyAdvancedStateControl` o nowe metadane właściwości. Na przykład, wartość domyślna `StateProperty` jest teraz `true` gdy właściwość jest poddawany kwerendzie na nowo utworzone `MyAdvancedStateControl` wystąpienia.  
  
 [!code-csharp[PropertySystemEsoterics#MyStateControl](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#mystatecontrol)]
 [!code-vb[PropertySystemEsoterics#MyStateControl](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#mystatecontrol)]  
[!code-csharp[PropertySystemEsoterics#MyAdvancedStateControl](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#myadvancedstatecontrol)]
[!code-vb[PropertySystemEsoterics#MyAdvancedStateControl](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#myadvancedstatecontrol)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.DependencyProperty>  
 [Przegląd właściwości zależności](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
 [Właściwości niestandardowe zależności](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)  
 [Tematy porad](../../../../docs/framework/wpf/advanced/properties-how-to-topics.md)

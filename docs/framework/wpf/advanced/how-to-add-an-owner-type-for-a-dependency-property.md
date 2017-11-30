---
title: "Jak dodać typ właściciela dla właściwości zależności"
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
- classes [WPF], adding as owners of dependency properties
- dependency properties [WPF], adding classes as owners of
ms.assetid: edcce050-0576-4edb-a31a-3f909637b452
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 079f08e1c330b710748ea6bb1aab8ccfb7ae7016
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-add-an-owner-type-for-a-dependency-property"></a>Jak dodać typ właściciela dla właściwości zależności
W tym przykładzie przedstawiono sposób dodawania klasy jako właściciela właściwości zależności zarejestrowany dla innego typu. Dzięki temu, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] czytnika właściwości systemu są i rozpoznawany jako właściciela dodatkowe właściwości klasy. Dodawanie jako właściciela opcjonalnie umożliwia dodawanie klasy do udostępnienia metadanych określonego typu.  
  
 W poniższym przykładzie `StateProperty` właściwość zarejestrowane przez `MyStateControl` klasy. Klasa `UnrelatedStateControl` dodaje się jako właściciel `StateProperty` przy użyciu <xref:System.Windows.DependencyProperty.AddOwner%2A> metody, w szczególności za pomocą podpisu, który zezwala na nowe metadane dla właściwości zależności, ponieważ znajduje się na dodawanie typu. Należy zauważyć, że należy zapewnić [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] metod dostępu właściwości, podobnie jak w przykładzie przedstawionym w [implementuje właściwości zależności](../../../../docs/framework/wpf/advanced/how-to-implement-a-dependency-property.md) przykład, jak również ponownie udostępnić identyfikatora właściwości zależności klasy dodawane jako właściciel.  
  
 Bez otoki, właściwości zależności będą nadal działać z punktu widzenia programowy dostęp przy użyciu <xref:System.Windows.DependencyObject.GetValue%2A> lub <xref:System.Windows.DependencyObject.SetValue%2A>. Ale zwykle można równoległe to zachowanie właściwości systemu z [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] otoki właściwości. Otoki ułatwić można ustawić właściwości zależności programowo i pozwala ustawić właściwości jako [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] atrybutów.  
  
 Aby dowiedzieć się, jak zastąpić domyślny metadanych, zobacz [zastąpienia metadane dla właściwości zależności](../../../../docs/framework/wpf/advanced/how-to-override-metadata-for-a-dependency-property.md).  
  
## <a name="example"></a>Przykład  
 [!code-csharp[PropertySystemEsoterics#MyStateControl](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#mystatecontrol)]
 [!code-vb[PropertySystemEsoterics#MyStateControl](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#mystatecontrol)]  
[!code-csharp[PropertySystemEsoterics#UnrelatedStateControl](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#unrelatedstatecontrol)]
[!code-vb[PropertySystemEsoterics#UnrelatedStateControl](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#unrelatedstatecontrol)]  
  
## <a name="see-also"></a>Zobacz też  
 [Właściwości niestandardowe zależności](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)  
 [Przegląd właściwości zależności](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)

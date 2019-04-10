---
title: 'Instrukcje: Dodawanie typu właściciela dla właściwości zależności'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- classes [WPF], adding as owners of dependency properties
- dependency properties [WPF], adding classes as owners of
ms.assetid: edcce050-0576-4edb-a31a-3f909637b452
ms.openlocfilehash: 1b1f2b241868b02e430af82bac8e9f6a617e511b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59217097"
---
# <a name="how-to-add-an-owner-type-for-a-dependency-property"></a>Instrukcje: Dodawanie typu właściciela dla właściwości zależności
W tym przykładzie przedstawiono sposób dodawania klasy jako właściciele właściwości zależności, zarejestrowany dla innego typu. Dzięki temu, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] czytnika i system właściwości są rozpoznawać klasy jako właściciel dodatkowe właściwości. Dodawanie jako właściciel opcjonalnie umożliwia dodanie klasy do udostępnienia metadanych specyficznych dla typu.  
  
 W poniższym przykładzie `StateProperty` właściwość zarejestrowane przez `MyStateControl` klasy. Klasa `UnrelatedStateControl` dodaje się jako właściciel `StateProperty` przy użyciu <xref:System.Windows.DependencyProperty.AddOwner%2A> metody, w szczególności za pomocą podpisu, umożliwiający nowe metadane dla właściwości zależności, ponieważ znajduje się na dodawanie typu. Należy zauważyć, że należy podać [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] metod dostępu właściwości, które są podobne do pokazanego poniżej [implementować właściwość zależności](how-to-implement-a-dependency-property.md) przykładu, a także ponownie udostępnić identyfikator właściwości zależności klasy dodawane jako właściciel.  
  
 Bez otoki, właściwość zależności będą nadal działać z punktu widzenia dostęp programowy przy użyciu <xref:System.Windows.DependencyObject.GetValue%2A> lub <xref:System.Windows.DependencyObject.SetValue%2A>. Jednak zazwyczaj równoległe tego zachowania system właściwości [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] otoki właściwości. Otoki ułatwić programowe Ustawianie właściwości zależności i umożliwia ustawianie właściwości jako [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] atrybutów.  
  
 Aby dowiedzieć się, jak zastąpić domyślny metadanych, zobacz [zastąpić metadane dla właściwości zależności](how-to-override-metadata-for-a-dependency-property.md).  
  
## <a name="example"></a>Przykład  
 [!code-csharp[PropertySystemEsoterics#MyStateControl](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#mystatecontrol)]
 [!code-vb[PropertySystemEsoterics#MyStateControl](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#mystatecontrol)]  
[!code-csharp[PropertySystemEsoterics#UnrelatedStateControl](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#unrelatedstatecontrol)]
[!code-vb[PropertySystemEsoterics#UnrelatedStateControl](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#unrelatedstatecontrol)]  
  
## <a name="see-also"></a>Zobacz także

- [Niestandardowe właściwości zależności](custom-dependency-properties.md)
- [Przegląd właściwości zależności](dependency-properties-overview.md)

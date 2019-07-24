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
ms.openlocfilehash: 5ddc85d159b4bf81751428c13c234c5e53be8ad4
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2019
ms.locfileid: "68401135"
---
# <a name="how-to-add-an-owner-type-for-a-dependency-property"></a>Instrukcje: Dodawanie typu właściciela dla właściwości zależności
Ten przykład pokazuje, jak dodać klasę jako właściciela właściwości zależności zarejestrowanej dla innego typu. W ten [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sposób czytnik i system właściwości mogą rozpoznać klasę jako dodatkowy właściciel właściwości. Dodanie jako właściciela opcjonalnie zezwala na dodawanie metadanych specyficznych dla typu dla klasy.  
  
 W poniższym przykładzie `StateProperty` jest właściwością zarejestrowana `MyStateControl` przez klasę. Klasa `UnrelatedStateControl` dodaje siebie jako właściciela `StateProperty` przy użyciu <xref:System.Windows.DependencyProperty.AddOwner%2A> metody, w odniesieniu do podpisu, który umożliwia nowe metadane dla właściwości zależności, która istnieje w typie Dodawanie. Należy zauważyć, że należy zapewnić dostęp do środowiska uruchomieniowego języka wspólnego (CLR) dla właściwości, podobnie jak w przykładzie pokazanym w przykładowym [implementacji właściwości zależności](how-to-implement-a-dependency-property.md) , a także ponownego uwidocznić identyfikator właściwości zależności w klasie dodawanej jako właściciel.  
  
 Bez otok, właściwość zależności nadal będzie współpracować z perspektywą dostępu programistycznego przy użyciu <xref:System.Windows.DependencyObject.GetValue%2A> lub. <xref:System.Windows.DependencyObject.SetValue%2A> Zwykle jednak ma to na celu równoległe zachowanie systemu właściwości przy użyciu otok właściwości środowiska CLR. Otoki ułatwiają programowo Ustawianie właściwości zależności i umożliwiają ustawianie właściwości jako [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] atrybutów.  
  
 Aby dowiedzieć się, jak zastąpić domyślne metadane, zobacz [przesłanianie metadanych dla właściwości zależności](how-to-override-metadata-for-a-dependency-property.md).  
  
## <a name="example"></a>Przykład  
 [!code-csharp[PropertySystemEsoterics#MyStateControl](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#mystatecontrol)]
 [!code-vb[PropertySystemEsoterics#MyStateControl](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#mystatecontrol)]  
[!code-csharp[PropertySystemEsoterics#UnrelatedStateControl](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#unrelatedstatecontrol)]
[!code-vb[PropertySystemEsoterics#UnrelatedStateControl](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#unrelatedstatecontrol)]  
  
## <a name="see-also"></a>Zobacz także

- [Niestandardowe właściwości zależności](custom-dependency-properties.md)
- [Przegląd właściwości zależności](dependency-properties-overview.md)

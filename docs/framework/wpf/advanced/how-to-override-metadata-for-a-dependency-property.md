---
title: 'Instrukcje: Przesłanianie metadanych dla właściwości zależności'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- metadata [WPF], overriding for dependency properties
- dependency properties [WPF], overriding metadata for
- overriding metadata for dependency properties [WPF]
ms.assetid: f90f026e-60d8-428a-933d-edf0dba4441f
ms.openlocfilehash: 7f20708722660aa4f86462efd50939935f840613
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59209440"
---
# <a name="how-to-override-metadata-for-a-dependency-property"></a>Instrukcje: Przesłanianie metadanych dla właściwości zależności
W tym przykładzie pokazano, jak zastąpić domyślny metadane zależności właściwości pochodzący z klasy dziedziczonej, wywołując <xref:System.Windows.DependencyProperty.OverrideMetadata%2A> metody i dostarczanie metadanych dla określonego typu.  
  
## <a name="example"></a>Przykład  
 Dzięki zdefiniowaniu jego <xref:System.Windows.PropertyMetadata>, klasę można zdefiniować zachowań właściwości zależności, takie jak jego domyślne wartości i właściwości systemu wywołań zwrotnych. Wiele klas właściwość zależności już metadanych domyślne ustanowiony jako część procesu rejestracji. Obejmuje to właściwości zależności, które są częścią [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)]. Klasa, która dziedziczy właściwości zależności za pomocą jego dziedziczenia klas można zastąpić odpowiednich oryginalnych metadanych, tak, aby właściwości właściwość, która może być zmienione za pomocą metadanych będzie odpowiadał wszelkie wymagania specyficzne dla podklasy.  
  
 Zastępowanie metadanych właściwości zależności, należy wykonać przed tej właściwości zostanie umieszczona w użyciu przez system właściwości (to jest równa czas określone wystąpienia obiektów, które rejestrują właściwości są tworzone). Wywołania <xref:System.Windows.DependencyProperty.OverrideMetadata%2A> muszą być wykonywane w konstruktorach statycznych typu, który zapewnia siebie jako `forType` parametru <xref:System.Windows.DependencyProperty.OverrideMetadata%2A>. Jeśli spróbujesz zmienić metadanych, gdy istnieje jedno wystąpienie typu właściciela, to nie generuje wyjątków, ale spowoduje zachowania niespójność w systemie właściwości. Ponadto metadanych tylko można zastąpić raz dla typu. Przesłanianie metadanych dla tego samego typu na kolejne próby zgłosi wyjątek.  
  
 W poniższym przykładzie klasa niestandardowa `MyAdvancedStateControl` metadanych określone zastąpienia `StateProperty` przez `MyAdvancedStateControl` o nowe metadane właściwości. Na przykład, wartość domyślna `StateProperty` jest teraz `true` gdy właściwość jest wysyłane zapytanie na nowo skonstruowany `MyAdvancedStateControl` wystąpienia.  
  
 [!code-csharp[PropertySystemEsoterics#MyStateControl](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#mystatecontrol)]
 [!code-vb[PropertySystemEsoterics#MyStateControl](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#mystatecontrol)]  
[!code-csharp[PropertySystemEsoterics#MyAdvancedStateControl](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#myadvancedstatecontrol)]
[!code-vb[PropertySystemEsoterics#MyAdvancedStateControl](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#myadvancedstatecontrol)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.DependencyProperty>
- [Przegląd właściwości zależności](dependency-properties-overview.md)
- [Niestandardowe właściwości zależności](custom-dependency-properties.md)
- [Tematy z instrukcjami](properties-how-to-topics.md)

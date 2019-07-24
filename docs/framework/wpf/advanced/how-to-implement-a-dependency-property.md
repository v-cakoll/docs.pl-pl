---
title: 'Instrukcje: Implementowanie właściwości zależności'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dependency properties [WPF], backing properties with
- properties [WPF], backing with dependency properties
ms.assetid: 855fd6d7-19ac-493c-bf5e-2f40b57cdc92
ms.openlocfilehash: 6f2fb9b0824feb6253527de063f58da2427d0c06
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2019
ms.locfileid: "68400359"
---
# <a name="how-to-implement-a-dependency-property"></a>Instrukcje: Implementowanie właściwości zależności
Ten przykład pokazuje, jak wykonać kopię zapasową właściwości środowiska uruchomieniowego języka wspólnego <xref:System.Windows.DependencyProperty> (CLR) za pomocą pola, w ten sposób definiując właściwość zależności. Podczas definiowania własnych właściwości i chcą one obsługiwać wiele aspektów [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] funkcjonalności, w tym style, powiązanie danych, dziedziczenie, animację i wartości domyślne, należy zaimplementować je jako właściwość zależności.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład najpierw rejestruje właściwość zależności przez wywołanie <xref:System.Windows.DependencyProperty.Register%2A> metody. Nazwa pola identyfikatora służącego do przechowywania nazwy i właściwości zależności musi być <xref:System.Windows.DependencyProperty.Name%2A> wybrana dla właściwości zależności jako część <xref:System.Windows.DependencyProperty.Register%2A> wywołania, dołączona przez ciąg `Property`literału. Na przykład jeśli zostanie zarejestrowana właściwość zależności z <xref:System.Windows.DependencyProperty.Name%2A> `Location`, wówczas pole identyfikatora zdefiniowane dla właściwości zależności musi mieć nazwę `LocationProperty`.  
  
 W tym przykładzie nazwa właściwości Dependency i jej metoda dostępu CLR `State`to; pole identyfikatora to `StateProperty`; typ właściwości to <xref:System.Boolean>;, a typ, który rejestruje właściwość zależności, to `MyStateControl`.  
  
 Jeśli ten wzorzec nazewnictwa nie zostanie zgodny, projektanci mogą nie zgłosić swojej właściwości prawidłowo, a niektóre aspekty aplikacji stylu systemu właściwości mogą nie zachowywać się zgodnie z oczekiwaniami.  
  
 Można również określić domyślne metadane dla właściwości zależności. Ten przykład rejestruje wartość `State` domyślną właściwości `false`zależności.  
  
 [!code-csharp[PropertySystemEsoterics#MyStateControl](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#mystatecontrol)]
 [!code-vb[PropertySystemEsoterics#MyStateControl](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#mystatecontrol)]  
  
 Aby uzyskać więcej informacji o tym, jak i dlaczego zaimplementować właściwość zależności, w przeciwieństwie do tylko wykonywania kopii zapasowej właściwości CLR z polem prywatnym, zobacz [Omówienie właściwości zależności](dependency-properties-overview.md).  
  
## <a name="see-also"></a>Zobacz także

- [Przegląd właściwości zależności](dependency-properties-overview.md)
- [Tematy z instrukcjami](properties-how-to-topics.md)

---
title: xml:space — Obsługa w XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], xml:space attribute
- XAML [XAML Services], white-space processing
- xml:space attribute [XAML Services]
- white-space processing [XAML Services]
ms.assetid: 5e1814f0-5b30-43d5-8c88-dede335a89d7
ms.openlocfilehash: a7c3775f2e49a80eabc61f24d086a94fcadfd574
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54617580"
---
# <a name="xmlspace-handling-in-xaml"></a>xml:space — Obsługa w XAML
`xml:space` Atrybut jest definiowany w języku XML atrybut deklarujący zachowanie przetwarzania odstępu w obrębie elementu obiektu. To zachowanie jest odpowiednie dla całej zawartości (tekst wewnętrzny) zawartych w elemencie gdzie `xml:space` jest zadeklarowana, a także zakresów do elementów podrzędnych.  
  
## <a name="xaml-attribute-usage"></a>Użycie atrybutu języka XAML  
  
```xaml  
<object xml:space="preserve" />  
```  
  
 \- lub —  
  
```xaml  
<object xml:space="default" />  
```  
  
## <a name="remarks"></a>Uwagi  
 Definicja `xml:space` atrybut w XAML, łącznie z jego dwóch wartości jest tworzony na podstawie `xml:space` zgodnie z definicją jako "specjalne atrybutu" specyfikacje W3C XML.  
  
 Wartość domyślna `xml:space` atrybut jest wartość literału `"default"`. Dla wartości `"default"`, lub jeśli `xml:space` nie wskazano, zachowanie analizowania znaczące odstępu jest domyślna obsługa, zgodnie z definicją w temacie [spacji w XAML na przetworzenie](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md).  
  
 Aby zachować biały znak w zawartości elementu obiektu, należy określić `xml:space="preserve"` w elemencie tego obiektu.  
  
 W większości interpretacji `xml:space` efekty atrybutem i wartością atrybutu są ograniczone do elementów podrzędnych.  
  
 Wyczerpujące omówienie odstępu, przetwarzanie w XAML, zobacz [spacji w XAML na przetworzenie](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md).  
  
## <a name="see-also"></a>Zobacz także
- [Znak odstępu przetwarzanie w XAML](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md)
- [Przegląd XAML (WPF)](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)

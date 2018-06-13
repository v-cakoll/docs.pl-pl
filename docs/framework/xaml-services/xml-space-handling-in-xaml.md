---
title: xml:space — Obsługa w XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], xml:space attribute
- XAML [XAML Services], whitespace processing
- xml:space attribute [XAML Services]
- whitespace processing [XAML Services]
ms.assetid: 5e1814f0-5b30-43d5-8c88-dede335a89d7
ms.openlocfilehash: af971ad9ea74e123b939ff8d8488e4e45c5d4aed
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33563470"
---
# <a name="xmlspace-handling-in-xaml"></a>xml:space — Obsługa w XAML
`xml:space` Atrybut jest definiowany w języku XML atrybut deklarujący zachowania przetwarzania znaczącym odstępem w elemencie obiektu. To zachowanie jest odpowiednie dla całej zawartości (tekst wewnętrzny) zawartych w elemencie gdzie `xml:space` jest zadeklarowana, a także zakresów do elementów podrzędnych.  
  
## <a name="xaml-attribute-usage"></a>Użycie atrybutu języka XAML  
  
```xaml  
<object xml:space="preserve" />  
```  
  
 \- lub -  
  
```xaml  
<object xml:space="default" />  
```  
  
## <a name="remarks"></a>Uwagi  
 Definicja `xml:space` atrybut w XAML, łącznie z jej dwa możliwe wartości jest pochodną `xml:space` zgodnie z definicją jako "specjalne atrybutu" specyfikacje W3C XML.  
  
 Wartość domyślna `xml:space` atrybut jest wartość literału `"default"`. Wartość `"default"`, lub jeśli `xml:space` nie wskazano, zachowanie podczas analizowania znaczące światła jest domyślna obsługa, zgodnie z definicją w temacie [przetwarzanie spacji w XAML](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md).  
  
 Aby zachować odstępów w obrębie obiektu elementu zawartości, określ `xml:space="preserve"` w tym elemencie obiektu.  
  
 W większości interpretacje `xml:space` efekty atrybutu, a wartość atrybutu ograniczone do elementów podrzędnych.  
  
 Aby uzyskać szczegółowe omówienie przetwarzanie spacji w XAML, zobacz [przetwarzanie spacji w XAML](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Przetwarzanie spacji w XAML](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md)  
 [Przegląd XAML (WPF)](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)

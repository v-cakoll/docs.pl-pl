---
title: "xml:space — Obsługa w XAML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XAML [XAML Services], xml:space attribute
- XAML [XAML Services], whitespace processing
- xml:space attribute [XAML Services]
- whitespace processing [XAML Services]
ms.assetid: 5e1814f0-5b30-43d5-8c88-dede335a89d7
caps.latest.revision: "15"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: a5048cbad1d2ea914d041ac3c87a43223b208c3a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="xmlspace-handling-in-xaml"></a>xml:space — Obsługa w XAML
`xml:space` Atrybut jest definiowany w języku XML atrybut deklarujący zachowania przetwarzania znaczącym odstępem w elemencie obiektu. To zachowanie jest odpowiednie dla całej zawartości (tekst wewnętrzny) zawartych w elemencie gdzie `xml:space` jest zadeklarowana, a także zakresów do elementów podrzędnych.  
  
## <a name="xaml-attribute-usage"></a>Użycie atrybutu języka XAML  
  
```xaml  
<object xml:space="preserve" />  
```  
  
 \-lub -  
  
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
 [Omówienie XAML (WPF)](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)

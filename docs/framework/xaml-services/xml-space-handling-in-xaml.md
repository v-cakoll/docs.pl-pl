---
title: xml:space — Obsługa w XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], xml:space attribute
- XAML [XAML Services], white-space processing
- xml:space attribute [XAML Services]
- white-space processing [XAML Services]
ms.assetid: 5e1814f0-5b30-43d5-8c88-dede335a89d7
ms.openlocfilehash: 8f860f5ee42b5c1df43c4ec2b1003408bc1c0d8e
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458793"
---
# <a name="xmlspace-handling-in-xaml"></a>xml:space — Obsługa w XAML
Atrybut `xml:space` jest atrybutem zdefiniowanym przez XML, który deklaruje znaczące zachowanie przetwarzania białych miejsc wewnątrz elementu obiektu. To zachowanie dotyczy całej zawartości (tekst wewnętrzny) zawartej w elemencie, gdzie `xml:space` jest zadeklarowana, a także zakresy do elementów podrzędnych.  
  
## <a name="xaml-attribute-usage"></a>Użycie atrybutu języka XAML  
  
```xaml  
<object xml:space="preserve" />  
```  
  
 \- lub-  
  
```xaml  
<object xml:space="default" />  
```  
  
## <a name="remarks"></a>Uwagi  
 Definicja atrybutu `xml:space` w języku XAML, w tym jej dwie możliwe wartości, pochodzi od `xml:space`, jak zdefiniowano jako "atrybut specjalny" przez specyfikacje W3C dla XML.  
  
 Wartość domyślna atrybutu `xml:space` jest wartością literału `"default"`. Dla wartości `"default"`, lub jeśli w ogóle nie określono `xml:space`, zachowanie znaczącej analizy białych znaków jest domyślną obsługą, zgodnie z definicją w temacie [Przetwarzanie bieli miejsca w języku XAML](whitespace-processing-in-xaml.md).  
  
 Aby zachować biały znak w zawartości elementu obiektu, należy określić `xml:space="preserve"` w tym elemencie obiektu.  
  
 W ramach większości interpretacji, `xml:space` efekty atrybutu i wartość atrybutu są zakresem elementów podrzędnych.  
  
 Aby uzyskać pełną dyskusję na temat przetwarzania białych miejsc w języku XAML, zobacz artykuł [Przetwarzanie białych miejsc w języku XAML](whitespace-processing-in-xaml.md).  
  
## <a name="see-also"></a>Zobacz także

- [Przetwarzanie białych miejsc w języku XAML](whitespace-processing-in-xaml.md)
- [Przegląd XAML (WPF)](../../desktop-wpf/fundamentals/xaml.md)

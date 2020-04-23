---
title: xml:space — Obsługa w XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], xml:space attribute
- XAML [XAML Services], white-space processing
- xml:space attribute [XAML Services]
- white-space processing [XAML Services]
ms.assetid: 5e1814f0-5b30-43d5-8c88-dede335a89d7
ms.openlocfilehash: 886f906b6d1e3a10920dbf52e36bf76324c5a9f2
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071438"
---
# <a name="xmlspace-handling-in-xaml"></a>xml:space — Obsługa w XAML

Atrybut `xml:space` jest atrybutem zdefiniowanym przez XML, który deklaruje znaczące zachowanie przetwarzania odstępu w elemencie obiektu. To zachowanie jest istotne dla całej zawartości (tekst `xml:space` wewnętrzny) zawarte w elemencie, gdzie jest zadeklarowany, a także zakresy do elementów podrzędnych.

## <a name="xaml-attribute-usage"></a>Użycie atrybutu języka XAML

```xaml
<object xml:space="preserve" />
```

 \-lub -

```xaml
<object xml:space="default" />
```

## <a name="remarks"></a>Uwagi

Definicja atrybutu `xml:space` w języku XAML, w tym `xml:space` jego dwie możliwe wartości, jest wyprowadzana jako zdefiniowana jako "atrybut specjalny" według specyfikacji W3C dla XML.

Domyślną wartością `xml:space` atrybutu jest wartość `"default"`literału . Dla wartości `"default"`, `xml:space` lub jeśli nie jest wskazany w ogóle, zachowanie znaczących analizowania odstępu jest domyślną obsługą, zgodnie z definicją w temacie [Przetwarzanie odstępu w XAML](white-space-processing.md).

Aby zachować odstępy w `xml:space="preserve"` zawartości elementu obiektu, należy określić w tym elemencie obiektu.

W większości interpretacji `xml:space` efekty atrybutu i wartość atrybutu są ograniczone do elementów podrzędnych.

Aby uzyskać pełną dyskusję na temat przetwarzania odstępów w języku XAML, zobacz [Przetwarzanie odstępów w języku XAML](white-space-processing.md).

## <a name="see-also"></a>Zobacz też

- [Przetwarzanie spacji w XAML](white-space-processing.md)
- [Omówienie XAML (WPF)](../fundamentals/xaml.md)

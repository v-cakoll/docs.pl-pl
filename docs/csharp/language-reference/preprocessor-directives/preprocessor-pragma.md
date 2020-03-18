---
title: '#pragma - C# Odwołanie'
ms.date: 07/20/2015
f1_keywords:
- '#pragma'
helpviewer_keywords:
- '#pragma directive [C#]'
ms.assetid: 5b7944cd-d402-46a1-ad8f-feffb2d83673
ms.openlocfilehash: 3bd62364aeae0f21715711324655ef7d00d88afc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712458"
---
# <a name="pragma-c-reference"></a>#pragma (odwołanie w C#)
`#pragma`daje kompilatorowi specjalne instrukcje dotyczące kompilacji pliku, w którym się pojawia. Instrukcje muszą być obsługiwane przez kompilator. Innymi słowy nie można `#pragma` użyć do tworzenia niestandardowych instrukcji wstępnego przetwarzania. Kompilator Języka Microsoft C# obsługuje następujące dwie `#pragma` instrukcje:  
  
 [#pragma warning](./preprocessor-pragma-warning.md)  
  
 [#pragma checksum](./preprocessor-pragma-checksum.md)  
  
## <a name="syntax"></a>Składnia  
  
```csharp
#pragma pragma-name pragma-arguments  
```  
  
## <a name="parameters"></a>Parametry  
 `pragma-name`  
 Nazwa uznanej pragmy.  
  
 `pragma-arguments`  
 Argumenty specyficzne dla Pragmy.  
  
## <a name="see-also"></a>Zobacz też

- [Odwołanie do języka C#](../index.md)
- [Przewodnik programowania języka C#](../../programming-guide/index.md)
- [Dyrektywy przedprocesorowe C#](./index.md)
- [#pragma warning](./preprocessor-pragma-warning.md)
- [#pragma checksum](./preprocessor-pragma-checksum.md)

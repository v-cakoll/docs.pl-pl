---
title: '#pragma — C# odwołania'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '#pragma'
helpviewer_keywords:
- '#pragma directive [C#]'
ms.assetid: 5b7944cd-d402-46a1-ad8f-feffb2d83673
ms.openlocfilehash: 8b39d6760a5e30986d5d4bbe9bb1281dbf6742a2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61689271"
---
# <a name="pragma-c-reference"></a>#pragma (odwołanie w C#)
Dyrektywa `#pragma` zapewnia specjalne instrukcje dla kompilatora dotyczące kompilowania pliku, w którym występuje. Instrukcje muszą być obsługiwane przez kompilator.  Innymi słowy, nie można użyć dyrektywy `#pragma` do tworzenia niestandardowych instrukcji przetwarzania wstępnego. Kompilator Microsoft C# obsługuje dwie instrukcje `#pragma`:  
  
 [#pragma warning](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md)  
  
 [#pragma checksum](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-checksum.md)  
  
## <a name="syntax"></a>Składnia  
  
```csharp
#pragma pragma-name pragma-arguments  
```  
  
## <a name="parameters"></a>Parametry  
 `pragma-name`  
 Nazwa rozpoznanej dyrektywy pragma.  
  
 `pragma-arguments`  
 Argumenty określone dla dyrektywy pragma.  
  
## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../../../csharp/language-reference/index.md)
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
- [Dyrektywy preprocesora C#](../../../csharp/language-reference/preprocessor-directives/index.md)
- [#pragma warning](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md)
- [#pragma checksum](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-checksum.md)

---
title: <remarks> - C# Przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- remarks
- <remarks>
helpviewer_keywords:
- remarks C# XML tag
- <remarks> C# XML tag
ms.assetid: f8641391-31f3-4735-af7a-c502a5b6a251
ms.openlocfilehash: b290315cd9c36281c110bbf0c6246468a1a899b2
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55259166"
---
# <a name="remarks-c-programming-guide"></a>\<Remarks > (C# Programming Guide)
## <a name="syntax"></a>Składnia  
  
```xml  
<remarks>description</remarks>  
```  
  
#### <a name="parameters"></a>Parametry  
 `Description`  
 Opis elementu członkowskiego.  
  
## <a name="remarks"></a>Uwagi  
 \<Uwagi > tag jest używany do dodawania informacji o typie, informacje uzupełniające określony za pomocą [ \<podsumowania >](../../../csharp/programming-guide/xmldoc/summary.md). Te informacje są wyświetlane w oknie przeglądarki obiektów.  
  
 Kompiluj przy użyciu [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) do Przetwarzaj komentarze dokumentacji do pliku.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csProgGuideDocComments#9](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/remarks_1.cs)]  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
- [Zalecane tagi przeznaczone do komentarzy dokumentacji](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)

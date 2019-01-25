---
title: '&lt;Uwagi&gt; - C# Programming Guide'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- remarks
- <remarks>
helpviewer_keywords:
- remarks C# XML tag
- <remarks> C# XML tag
ms.assetid: f8641391-31f3-4735-af7a-c502a5b6a251
ms.openlocfilehash: faeb1b07d4778f56ae854d5ece93588cbe5848f6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54536051"
---
# <a name="ltremarksgt-c-programming-guide"></a>&lt;Uwagi&gt; (C# Programming Guide)
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

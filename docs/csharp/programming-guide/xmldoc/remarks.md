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
ms.openlocfilehash: 3e6625c55a6f5c29fb55bff2eb87959f3237652e
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56975860"
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
 [!code-csharp[csProgGuideDocComments#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#9)]  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
- [Zalecane tagi przeznaczone do komentarzy dokumentacji](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)

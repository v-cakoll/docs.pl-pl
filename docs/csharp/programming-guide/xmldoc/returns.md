---
title: <returns> — C# Przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- returns
- <returns>
helpviewer_keywords:
- <returns> C# XML tag
- returns C# XML tag
ms.assetid: bb2d9958-62fc-47c7-9511-6311171f119f
ms.openlocfilehash: 7d4343cf38f0ea1ae42b77cc1d0c755920c4a421
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69587733"
---
# <a name="returns-c-programming-guide"></a>\<zwraca > (C# Przewodnik programowania)
## <a name="syntax"></a>Składnia  
  
```xml  
<returns>description</returns>  
```  
  
## <a name="parameters"></a>Parametry  
 `description`  
 Opis wartości zwracanej.  
  
## <a name="remarks"></a>Uwagi  
 Tag \<Returns > powinien zostać użyty w komentarzu dla deklaracji metody, aby opisać wartość zwracaną.  
  
 Kompiluj z [/doc](../../language-reference/compiler-options/doc-compiler-option.md) , aby przetwarzać komentarze dokumentacji do pliku.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csProgGuideDocComments#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#10)]  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Zalecane tagi przeznaczone do komentarzy dokumentacji](./recommended-tags-for-documentation-comments.md)

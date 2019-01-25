---
title: '&lt;c&gt; - C# przewodnik programowania'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- c
- <c>
helpviewer_keywords:
- text, marking as code [C#]
- code, marking text as [C#]
- c C# XML tag
- <c> C# XML tag
ms.assetid: aad5b16e-a29e-445e-bd0d-eea0b138d7b2
ms.openlocfilehash: b789b95c5e23534fb36613ac9203f146b265a98d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54640988"
---
# <a name="ltcgt-c-programming-guide"></a>&lt;c&gt; (C# Programming Guide)
## <a name="syntax"></a>Składnia  
  
```xml  
<c>text</c>  
```  
  
#### <a name="parameters"></a>Parametry  
 `text`  
 Tekst, który chcesz wskazać jako kod.  
  
## <a name="remarks"></a>Uwagi  
 \<c > tag zapewnia sposób, aby wskazać, że tekst w opis powinien być oznaczony jako kod. Użyj [ \<kodu >](../../../csharp/programming-guide/xmldoc/code.md) aby wskazać wiele wierszy, jako kod.  
  
 Kompiluj przy użyciu [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) do Przetwarzaj komentarze dokumentacji do pliku.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csProgGuideDocComments#2](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/code-inline_1.cs)]  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
- [Zalecane tagi przeznaczone do komentarzy dokumentacji](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)

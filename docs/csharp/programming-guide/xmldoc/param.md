---
title: '&lt;param&gt; (C# przewodnik programowania w języku)'
ms.date: 07/20/2015
f1_keywords:
- param
- <param>
helpviewer_keywords:
- <param> C# XML tag
- param C# XML tag
ms.assetid: 46d329b1-5b84-4537-9e17-73ca97313e4e
ms.openlocfilehash: 3d89637e5b1238c582390750e8eef30960fa90b6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33338016"
---
# <a name="ltparamgt-c-programming-guide"></a>&lt;param&gt; (C# przewodnik programowania w języku)
## <a name="syntax"></a>Składnia  
  
```xml  
<param name="name">description</param>  
```  
  
#### <a name="parameters"></a>Parametry  
 `name`  
 Nazwa parametru metody. Nazwę należy ująć w podwójny cudzysłów ("").  
  
 `description`  
 Opis parametru.  
  
## <a name="remarks"></a>Uwagi  
 \<Param > tag powinny być używane w komentarz dla deklaracji metody opisujący jeden z parametrów metody. Aby udokumentować wiele parametrów, używanych jest wiele \<param > tagów.  
  
 Tekst dla \<param > będą wyświetlane w funkcji IntelliSense, przeglądarka obiektów i w raporcie Web komentarz kodu.  
  
 Kompiluj z użyciem [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) na przetwarzanie komentarzy dokumentacji do pliku.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csProgGuideDocComments#1](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/param_1.cs)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Zalecane tagi przeznaczone do komentarzy dokumentacji](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)

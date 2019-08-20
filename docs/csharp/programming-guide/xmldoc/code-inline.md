---
title: <c>— C# Przewodnik programowania
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
ms.openlocfilehash: c881b9ec577fb04381f9e10c7df8f9d0da44cd66
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69588185"
---
# <a name="c-c-programming-guide"></a>\<c > (C# Przewodnik programowania)
## <a name="syntax"></a>Składnia  
  
```xml  
<c>text</c>  
```  
  
## <a name="parameters"></a>Parametry  
 `text`  
 Tekst, który ma być wskazywany jako kod.  
  
## <a name="remarks"></a>Uwagi  
 Tag \<c > umożliwia wskazanie, że tekst w opisie powinien być oznaczony jako kod. [ Użyj\<> kodu](./code.md) , aby wskazać wiele wierszy jako kod.  
  
 Kompiluj z [/doc](../../language-reference/compiler-options/doc-compiler-option.md) , aby przetwarzać komentarze dokumentacji do pliku.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csProgGuideDocComments#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#2)]  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Zalecane tagi przeznaczone do komentarzy dokumentacji](./recommended-tags-for-documentation-comments.md)

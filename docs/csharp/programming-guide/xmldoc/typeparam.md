---
title: <typeparam> — C# Przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- typeparam
helpviewer_keywords:
- <typeparam> C# XML tag
- typeparam C# XML tag
ms.assetid: 9b99d400-e911-4e55-99c6-64367c96aa4f
ms.openlocfilehash: ea48cf0cdfc2dc48ad29ab6219449f801739bc8f
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69587593"
---
# <a name="typeparam-c-programming-guide"></a>\<typeparam > (C# Przewodnik programowania)
## <a name="syntax"></a>Składnia  
  
```xml  
<typeparam name="name">description</typeparam>  
```  
  
## <a name="parameters"></a>Parametry  
 `name`  
 Nazwa parametru typu. Ujmij nazwę w znaki podwójnego cudzysłowu ("").  
  
 `description`  
 Opis parametru typu.  
  
## <a name="remarks"></a>Uwagi  
 `<typeparam>` Tag powinien być używany w komentarzu dla typu ogólnego lub deklaracji metody, aby opisać parametr typu. Dodaj tag dla każdego parametru typu ogólnego typu lub metody.  
  
 Aby uzyskać więcej informacji, zobacz [Ogólne](../generics/index.md).  
  
 Tekst dla `<typeparam>` tagu będzie wyświetlany w IntelliSense, raport sieci Web przeglądarka obiektówgo komentarza do kodu [okna](/visualstudio/ide/viewing-the-structure-of-code#BKMK_ObjectBrowser) .  
  
 Kompiluj z [/doc](../../language-reference/compiler-options/doc-compiler-option.md) , aby przetwarzać komentarze dokumentacji do pliku.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csProgGuideDocComments#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#13)]  
  
## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../../language-reference/index.md)
- [Przewodnik programowania w języku C#](../index.md)
- [Zalecane tagi przeznaczone do komentarzy dokumentacji](./recommended-tags-for-documentation-comments.md)

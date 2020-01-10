---
title: <typeparam> — C# Przewodnik programowania
ms.date: 07/20/2015
f1_keywords:
- typeparam
helpviewer_keywords:
- <typeparam> C# XML tag
- typeparam C# XML tag
ms.assetid: 9b99d400-e911-4e55-99c6-64367c96aa4f
ms.openlocfilehash: 04145b82cbed0e9a5cae38ff9ef33d061ee792c9
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75694533"
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
 Tag `<typeparam>` powinien być używany w komentarzu dla typu ogólnego lub deklaracji metody, aby opisać parametr typu. Dodaj tag dla każdego parametru typu ogólnego typu lub metody.  
  
 Aby uzyskać więcej informacji, zobacz [Ogólne](../generics/index.md).  
  
 Tekst dla tagu `<typeparam>` będzie wyświetlany w technologii IntelliSense, Raport internetowy programu [Przeglądarka obiektów](/visualstudio/ide/viewing-the-structure-of-code#BKMK_ObjectBrowser) komentarzy do kodu okna.  
  
 Kompiluj z [-doc](../../language-reference/compiler-options/doc-compiler-option.md) , aby przetwarzać komentarze dokumentacji do pliku.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csProgGuideDocComments#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#13)]  
  
## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../../language-reference/index.md)
- [Przewodnik programowania w języku C#](../index.md)
- [Zalecane tagi przeznaczone do komentarzy dokumentacji](./recommended-tags-for-documentation-comments.md)

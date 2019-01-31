---
title: <typeparam> - C# Przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- typeparam
helpviewer_keywords:
- <typeparam> C# XML tag
- typeparam C# XML tag
ms.assetid: 9b99d400-e911-4e55-99c6-64367c96aa4f
ms.openlocfilehash: 08f9cf42f32c48e5dca09fc1141c55f6ba8af109
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55266276"
---
# <a name="typeparam-c-programming-guide"></a>\<typeparam > (C# Programming Guide)
## <a name="syntax"></a>Składnia  
  
```xml  
<typeparam name="name">description</typeparam>  
```  
  
#### <a name="parameters"></a>Parametry  
 `name`  
 Nazwa parametru typu. Nazwę należy ująć w znaki podwójnego cudzysłowu ("").  
  
 `description`  
 Opis parametru typu.  
  
## <a name="remarks"></a>Uwagi  
 `<typeparam>` Używany tag w komentarzu do deklaracji ogólnej typie lub metodzie do opisania parametrem typu. Dodaj tag dla każdego typu parametru typu ogólnego lub metody.  
  
 Aby uzyskać więcej informacji, zobacz [ogólne](../../../csharp/programming-guide/generics/index.md).  
  
 Tekst dla `<typeparam>` będą wyświetlane w technologii IntelliSense, [okna przeglądarki obiektów](/visualstudio/ide/viewing-the-structure-of-code#BKMK_ObjectBrowser) kodu komentarza raport sieci web.  
  
 Kompiluj przy użyciu [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) do Przetwarzaj komentarze dokumentacji do pliku.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csProgGuideDocComments#13](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/typeparam_1.cs)]  
  
## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../../../csharp/language-reference/index.md)
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
- [Zalecane tagi przeznaczone do komentarzy dokumentacji](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)

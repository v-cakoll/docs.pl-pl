---
title: "&lt;typeparam&gt; (C# przewodnik programowania w języku)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: typeparam
helpviewer_keywords:
- <typeparam> C# XML tag
- typeparam C# XML tag
ms.assetid: 9b99d400-e911-4e55-99c6-64367c96aa4f
caps.latest.revision: "19"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 6b9b81883d6d8abb960eda54f5c435acab6310b2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="lttypeparamgt-c-programming-guide"></a>&lt;typeparam&gt; (C# przewodnik programowania w języku)
## <a name="syntax"></a>Składnia  
  
```xml  
<typeparam name="name">description</typeparam>  
```  
  
#### <a name="parameters"></a>Parametry  
 `name`  
 Nazwa parametru typu. Nazwę należy ująć w podwójny cudzysłów ("").  
  
 `description`  
 Opis parametru typu.  
  
## <a name="remarks"></a>Uwagi  
 `<typeparam>` Tag powinny być używane w komentarz ogólny deklaracji typu lub metody do opisywania parametru typu. Dodaj tag dla każdego typu parametru typu ogólnego lub metody.  
  
 Aby uzyskać więcej informacji, zobacz [ogólne](../../../csharp/programming-guide/generics/index.md).  
  
 Tekst dla `<typeparam>` będą wyświetlane w IntelliSense, [okna przeglądarki obiektów](http://msdn.microsoft.com/en-us/3c7f1673-1f0d-41b1-94ca-a3dcfcb82cda) kodu — raport w sieci web komentarza.  
  
 Kompiluj z użyciem [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) na przetwarzanie komentarzy dokumentacji do pliku.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csProgGuideDocComments#13](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/typeparam_1.cs)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Zalecane tagi przeznaczone do komentarzy dokumentacji](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)

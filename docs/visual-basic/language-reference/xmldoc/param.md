---
title: <param>
ms.date: 07/20/2015
helpviewer_keywords:
- param XML tag
- <param> XML tag
ms.assetid: 4e32e86f-f6f3-4301-b7fc-2f321fb54368
ms.openlocfilehash: d325d5f9fbfd132630cf280653be214a267a7a80
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400063"
---
# <a name="param-visual-basic"></a>\<param> (Visual Basic)
Definiuje nazwę i opis parametru.  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<param name="name">description</param>  
```  
  
## <a name="parameters"></a>Parametry  
 `name`  
 Nazwa parametru metody. Ujmij nazwę w znaki podwójnego cudzysłowu ("").  
  
 `description`  
 Opis parametru.  
  
## <a name="remarks"></a>Uwagi  
 `<param>`Tag powinien być używany w komentarzu dla deklaracji metody, aby opisać jeden z parametrów dla metody.  
  
 Tekst dla `<param>` tagu pojawi się w następujących lokalizacjach:  
  
- Informacje o parametrach funkcji IntelliSense. Aby uzyskać więcej informacji, zobacz [Korzystanie z funkcji IntelliSense](/visualstudio/ide/using-intellisense).  
  
- Przeglądarka obiektów. Aby uzyskać więcej informacji, zobacz [Wyświetlanie struktury kodu](/visualstudio/ide/viewing-the-structure-of-code).  
  
 Kompiluj z [-doc](../../reference/command-line-compiler/doc.md) , aby przetwarzać komentarze dokumentacji do pliku.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie używa `<param>` znacznika do opisania `id` parametru.  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>Zobacz też

- [Tagi komentarza XML](index.md)

---
title: <typeparam> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- typeparam XML tag
- <typeparam> XML tag
ms.assetid: 1bb5ba78-f060-478c-905c-77a2e43639af
ms.openlocfilehash: 9e07a0c9d100669215f01a168da98902644a6f0b
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57496147"
---
# <a name="typeparam-visual-basic"></a>\<typeparam > (Visual Basic)
Definiuje typ parametru nazwę i opis.  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<typeparam name="name">description</typeparam>  
```  
  
## <a name="parameters"></a>Parametry  
 `name`  
 Nazwa parametru typu. Nazwę należy ująć w znaki podwójnego cudzysłowu ("").  
  
 `description`  
 Opis parametru typu.  
  
## <a name="remarks"></a>Uwagi  
 Użyj `<typeparam>` tagu w komentarz dla typu ogólnego lub deklaracji ogólnej składowej, opisujący jeden z parametrów typu.  
  
 Kompiluj przy użyciu [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) do Przetwarzaj komentarze dokumentacji do pliku.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto `<typeparam>` tag do opisania `id` parametru.  
  
 [!code-vb[VbVbcnXmlDocComments#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#8)]  
  
## <a name="see-also"></a>Zobacz także
- [Tagi komentarza XML](../../../visual-basic/language-reference/xmldoc/index.md)

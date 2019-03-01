---
title: <exception> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- <exception> XML tag
- exception XML tag
ms.assetid: c0517549-171e-4dae-ab88-a9c1700b6eee
ms.openlocfilehash: 157287ce5c85ec51f1711934cf9a5e4f568957ef
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56977191"
---
# <a name="exception-visual-basic"></a>\<wyjątek > (Visual Basic)
Określa, które wyjątki mogą zostać wygenerowane.  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<exception cref="member">description</exception>  
```  
  
#### <a name="parameters"></a>Parametry  
 `member`  
 Odwołanie do wyjątek, który jest dostępny w bieżącym środowisku kompilacji. Kompilator sprawdza, czy dany wyjątek istnieje i czy tłumaczy `member` nazwę kanoniczną element w danych wyjściowych XML. `member` musi znajdować się w znaki podwójnego cudzysłowu ("").  
  
 `description`  
 Opis.  
  
## <a name="remarks"></a>Uwagi  
 Użyj `<exception>` tag, aby określić, które wyjątki mogą zostać wygenerowane. Ten tag jest stosowany do definicji metody.  
  
 Kompiluj przy użyciu [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) do Przetwarzaj komentarze dokumentacji do pliku.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto `<exception>` znaczników do opisu wyjątku, `IntDivide` funkcja może zgłosić.  
  
 [!code-vb[VbVbcnXmlDocComments#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#3)]  
  
## <a name="see-also"></a>Zobacz także
- [Tagi komentarza XML](../../../visual-basic/language-reference/xmldoc/index.md)

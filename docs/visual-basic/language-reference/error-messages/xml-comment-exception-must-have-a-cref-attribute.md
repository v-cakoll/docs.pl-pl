---
title: Wyjątek komentarza XML musi mieć atrybut „cref”
ms.date: 07/20/2015
f1_keywords:
- bc42319
- vbc42319
helpviewer_keywords:
- BC42319
ms.assetid: 62eeeba3-6811-48be-b1ef-c2e4feda3177
ms.openlocfilehash: 54965f3796b6c5ef0e387cd354abcb5740476257
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72321174"
---
# <a name="xml-comment-exception-must-have-a-cref-attribute"></a><span data-ttu-id="36424-102">Wyjątek komentarza XML musi mieć atrybut „cref”</span><span class="sxs-lookup"><span data-stu-id="36424-102">XML comment exception must have a 'cref' attribute</span></span>

<span data-ttu-id="36424-103">Tag \<exception > umożliwia dokumentowanie wyjątków, które mogą być zgłaszane przez metodę.</span><span class="sxs-lookup"><span data-stu-id="36424-103">The \<exception> tag provides a way to document the exceptions that may be thrown by a method.</span></span> <span data-ttu-id="36424-104">Wymagany atrybut `cref` Określa nazwę elementu członkowskiego, który jest sprawdzany przez generator dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="36424-104">The required `cref` attribute designates the name of a member, which is checked by the documentation generator.</span></span> <span data-ttu-id="36424-105">Jeśli element członkowski istnieje, jest tłumaczony na nazwę elementu kanonicznego w pliku dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="36424-105">If the member exists, it is translated to the canonical element name in the documentation file.</span></span>

<span data-ttu-id="36424-106">**Identyfikator błędu:** BC42319</span><span class="sxs-lookup"><span data-stu-id="36424-106">**Error ID:** BC42319</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="36424-107">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="36424-107">To correct this error</span></span>

<span data-ttu-id="36424-108">Dodaj atrybut `cref` do wyjątku w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="36424-108">Add the `cref` attribute to the exception as follows:</span></span>

```xml
<exception cref="member">description</exception>
```

## <a name="see-also"></a><span data-ttu-id="36424-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="36424-109">See also</span></span>

- [<span data-ttu-id="36424-110">@no__t — 1exception ></span><span class="sxs-lookup"><span data-stu-id="36424-110">\<exception></span></span>](../../../visual-basic/language-reference/xmldoc/exception.md)
- [<span data-ttu-id="36424-111">Instrukcje: tworzenie dokumentacji XML</span><span class="sxs-lookup"><span data-stu-id="36424-111">How to: Create XML Documentation</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
- [<span data-ttu-id="36424-112">Tagi komentarza XML</span><span class="sxs-lookup"><span data-stu-id="36424-112">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)

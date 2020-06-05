---
title: Wyjątek komentarza XML musi mieć atrybut „cref”
ms.date: 07/20/2015
f1_keywords:
- bc42319
- vbc42319
helpviewer_keywords:
- BC42319
ms.assetid: 62eeeba3-6811-48be-b1ef-c2e4feda3177
ms.openlocfilehash: c498675ab6ae616fb63d3d76ef60bcac7e247145
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406511"
---
# <a name="xml-comment-exception-must-have-a-cref-attribute"></a><span data-ttu-id="15da8-102">Wyjątek komentarza XML musi mieć atrybut „cref”</span><span class="sxs-lookup"><span data-stu-id="15da8-102">XML comment exception must have a 'cref' attribute</span></span>

<span data-ttu-id="15da8-103">\<exception>Tag umożliwia dokumentowanie wyjątków, które mogą być zgłaszane przez metodę.</span><span class="sxs-lookup"><span data-stu-id="15da8-103">The \<exception> tag provides a way to document the exceptions that may be thrown by a method.</span></span> <span data-ttu-id="15da8-104">Wymagany `cref` atrybut określa nazwę elementu członkowskiego, który jest sprawdzany przez generator dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="15da8-104">The required `cref` attribute designates the name of a member, which is checked by the documentation generator.</span></span> <span data-ttu-id="15da8-105">Jeśli element członkowski istnieje, jest tłumaczony na nazwę elementu kanonicznego w pliku dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="15da8-105">If the member exists, it is translated to the canonical element name in the documentation file.</span></span>

<span data-ttu-id="15da8-106">**Identyfikator błędu:** BC42319</span><span class="sxs-lookup"><span data-stu-id="15da8-106">**Error ID:** BC42319</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="15da8-107">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="15da8-107">To correct this error</span></span>

<span data-ttu-id="15da8-108">Dodaj `cref` atrybut do wyjątku w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="15da8-108">Add the `cref` attribute to the exception as follows:</span></span>

```xml
<exception cref="member">description</exception>
```

## <a name="see-also"></a><span data-ttu-id="15da8-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="15da8-109">See also</span></span>

- [\<exception>](../xmldoc/exception.md)
- [<span data-ttu-id="15da8-110">Instrukcje: tworzenie dokumentacji XML</span><span class="sxs-lookup"><span data-stu-id="15da8-110">How to: Create XML Documentation</span></span>](../../programming-guide/program-structure/how-to-create-xml-documentation.md)
- [<span data-ttu-id="15da8-111">Tagi komentarza XML</span><span class="sxs-lookup"><span data-stu-id="15da8-111">XML Comment Tags</span></span>](../xmldoc/index.md)

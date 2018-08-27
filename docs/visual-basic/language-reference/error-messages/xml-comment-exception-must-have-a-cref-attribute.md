---
title: Wyjątek komentarza XML musi mieć &#39;cref&#39; atrybutu
ms.date: 07/20/2015
f1_keywords:
- bc42319
- vbc42319
helpviewer_keywords:
- BC42319
ms.assetid: 62eeeba3-6811-48be-b1ef-c2e4feda3177
ms.openlocfilehash: abe9fe0f6216f81fa223fe83a122b580577e1c32
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/26/2018
ms.locfileid: "42930031"
---
# <a name="xml-comment-exception-must-have-a-39cref39-attribute"></a><span data-ttu-id="9bacc-102">Wyjątek komentarza XML musi mieć &#39;cref&#39; atrybutu</span><span class="sxs-lookup"><span data-stu-id="9bacc-102">XML comment exception must have a &#39;cref&#39; attribute</span></span>
<span data-ttu-id="9bacc-103">\<Wyjątku > tag umożliwia dokumentowanie wyjątki, które mogą być generowane przez metodę.</span><span class="sxs-lookup"><span data-stu-id="9bacc-103">The \<exception> tag provides a way to document the exceptions that may be thrown by a method.</span></span> <span data-ttu-id="9bacc-104">Wymagane `cref` atrybut określa nazwę elementu członkowskiego, która jest sprawdzana przez generator dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="9bacc-104">The required `cref` attribute designates the name of a member, which is checked by the documentation generator.</span></span> <span data-ttu-id="9bacc-105">Jeśli istnieje elementu członkowskiego, jest tłumaczony nazwy kanonicznej elementu w pliku dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="9bacc-105">If the member exists, it is translated to the canonical element name in the documentation file.</span></span>  
  
 <span data-ttu-id="9bacc-106">**Identyfikator błędu:** BC42319</span><span class="sxs-lookup"><span data-stu-id="9bacc-106">**Error ID:** BC42319</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="9bacc-107">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="9bacc-107">To correct this error</span></span>  
  
-   <span data-ttu-id="9bacc-108">Dodaj `cref` atrybutu wyjątku w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="9bacc-108">Add the `cref` attribute to the exception as follows:</span></span>  
  
    ```  
    '''<exception cref="member">description</exception>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="9bacc-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9bacc-109">See Also</span></span>  
 [<span data-ttu-id="9bacc-110">\<wyjątku ></span><span class="sxs-lookup"><span data-stu-id="9bacc-110">\<exception></span></span>](../../../visual-basic/language-reference/xmldoc/exception.md)  
 [<span data-ttu-id="9bacc-111">Instrukcje: tworzenie dokumentacji XML</span><span class="sxs-lookup"><span data-stu-id="9bacc-111">How to: Create XML Documentation</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)  
 [<span data-ttu-id="9bacc-112">Tagi komentarza XML</span><span class="sxs-lookup"><span data-stu-id="9bacc-112">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)

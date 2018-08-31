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
ms.sourcegitcommit: fe02afbc39e78afd78cc6050e4a9c12a75f579f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/30/2018
ms.locfileid: "43255648"
---
# <a name="xml-comment-exception-must-have-a-39cref39-attribute"></a><span data-ttu-id="a7505-102">Wyjątek komentarza XML musi mieć &#39;cref&#39; atrybutu</span><span class="sxs-lookup"><span data-stu-id="a7505-102">XML comment exception must have a &#39;cref&#39; attribute</span></span>
<span data-ttu-id="a7505-103">\<Wyjątku > tag umożliwia dokumentowanie wyjątki, które mogą być generowane przez metodę.</span><span class="sxs-lookup"><span data-stu-id="a7505-103">The \<exception> tag provides a way to document the exceptions that may be thrown by a method.</span></span> <span data-ttu-id="a7505-104">Wymagane `cref` atrybut określa nazwę elementu członkowskiego, która jest sprawdzana przez generator dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="a7505-104">The required `cref` attribute designates the name of a member, which is checked by the documentation generator.</span></span> <span data-ttu-id="a7505-105">Jeśli istnieje elementu członkowskiego, jest tłumaczony nazwy kanonicznej elementu w pliku dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="a7505-105">If the member exists, it is translated to the canonical element name in the documentation file.</span></span>  
  
 <span data-ttu-id="a7505-106">**Identyfikator błędu:** BC42319</span><span class="sxs-lookup"><span data-stu-id="a7505-106">**Error ID:** BC42319</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a7505-107">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="a7505-107">To correct this error</span></span>  
  
-   <span data-ttu-id="a7505-108">Dodaj `cref` atrybutu wyjątku w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="a7505-108">Add the `cref` attribute to the exception as follows:</span></span>  
  
    ```  
    '''<exception cref="member">description</exception>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="a7505-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a7505-109">See Also</span></span>  
 [<span data-ttu-id="a7505-110">\<wyjątku ></span><span class="sxs-lookup"><span data-stu-id="a7505-110">\<exception></span></span>](../../../visual-basic/language-reference/xmldoc/exception.md)  
 [<span data-ttu-id="a7505-111">Instrukcje: tworzenie dokumentacji XML</span><span class="sxs-lookup"><span data-stu-id="a7505-111">How to: Create XML Documentation</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)  
 [<span data-ttu-id="a7505-112">Tagi komentarza XML</span><span class="sxs-lookup"><span data-stu-id="a7505-112">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)

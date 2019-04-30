---
title: Wyjątek komentarza XML musi mieć atrybut „cref”
ms.date: 07/20/2015
f1_keywords:
- bc42319
- vbc42319
helpviewer_keywords:
- BC42319
ms.assetid: 62eeeba3-6811-48be-b1ef-c2e4feda3177
ms.openlocfilehash: a974df5d2305b88946981d0d258a8088b23d3fc3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61766613"
---
# <a name="xml-comment-exception-must-have-a-cref-attribute"></a><span data-ttu-id="583ce-102">Wyjątek komentarza XML musi mieć atrybut „cref”</span><span class="sxs-lookup"><span data-stu-id="583ce-102">XML comment exception must have a 'cref' attribute</span></span>
<span data-ttu-id="583ce-103">\<Wyjątku > tag umożliwia dokumentowanie wyjątki, które mogą być generowane przez metodę.</span><span class="sxs-lookup"><span data-stu-id="583ce-103">The \<exception> tag provides a way to document the exceptions that may be thrown by a method.</span></span> <span data-ttu-id="583ce-104">Wymagane `cref` atrybut określa nazwę elementu członkowskiego, która jest sprawdzana przez generator dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="583ce-104">The required `cref` attribute designates the name of a member, which is checked by the documentation generator.</span></span> <span data-ttu-id="583ce-105">Jeśli istnieje elementu członkowskiego, jest tłumaczony nazwy kanonicznej elementu w pliku dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="583ce-105">If the member exists, it is translated to the canonical element name in the documentation file.</span></span>  
  
 <span data-ttu-id="583ce-106">**Identyfikator błędu:** BC42319</span><span class="sxs-lookup"><span data-stu-id="583ce-106">**Error ID:** BC42319</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="583ce-107">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="583ce-107">To correct this error</span></span>  
  
- <span data-ttu-id="583ce-108">Dodaj `cref` atrybutu wyjątku w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="583ce-108">Add the `cref` attribute to the exception as follows:</span></span>  
  
    ```  
    '''<exception cref="member">description</exception>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="583ce-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="583ce-109">See also</span></span>

- [<span data-ttu-id="583ce-110">\<wyjątku ></span><span class="sxs-lookup"><span data-stu-id="583ce-110">\<exception></span></span>](../../../visual-basic/language-reference/xmldoc/exception.md)
- [<span data-ttu-id="583ce-111">Instrukcje: Tworzenie dokumentacji XML</span><span class="sxs-lookup"><span data-stu-id="583ce-111">How to: Create XML Documentation</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
- [<span data-ttu-id="583ce-112">Tagi komentarza XML</span><span class="sxs-lookup"><span data-stu-id="583ce-112">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)

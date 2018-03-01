---
title: "Wyjątek komentarza XML musi mieć &#39; cref &#39; atrybut"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc42319
- vbc42319
helpviewer_keywords:
- BC42319
ms.assetid: 62eeeba3-6811-48be-b1ef-c2e4feda3177
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c0c22c9cd9415faf17d027c3751d166662a92b50
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="xml-comment-exception-must-have-a-39cref39-attribute"></a><span data-ttu-id="16ea3-102">Wyjątek komentarza XML musi mieć &#39; cref &#39; atrybut</span><span class="sxs-lookup"><span data-stu-id="16ea3-102">XML comment exception must have a &#39;cref&#39; attribute</span></span>
<span data-ttu-id="16ea3-103">\<Wyjątku > tagu umożliwia dokumentu wyjątki, które może zostać zgłoszony przez metodę.</span><span class="sxs-lookup"><span data-stu-id="16ea3-103">The \<exception> tag provides a way to document the exceptions that may be thrown by a method.</span></span> <span data-ttu-id="16ea3-104">Wymagane `cref` atrybut określa nazwę elementu członkowskiego, który jest sprawdzana przez generator dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="16ea3-104">The required `cref` attribute designates the name of a member, which is checked by the documentation generator.</span></span> <span data-ttu-id="16ea3-105">Jeśli istnieje element członkowski, są tłumaczone na nazwę kanoniczną elementu w pliku dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="16ea3-105">If the member exists, it is translated to the canonical element name in the documentation file.</span></span>  
  
 <span data-ttu-id="16ea3-106">**Identyfikator błędu:** BC42319</span><span class="sxs-lookup"><span data-stu-id="16ea3-106">**Error ID:** BC42319</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="16ea3-107">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="16ea3-107">To correct this error</span></span>  
  
-   <span data-ttu-id="16ea3-108">Dodaj `cref` atrybutu wyjątek w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="16ea3-108">Add the `cref` attribute to the exception as follows:</span></span>  
  
    ```  
    '''<exception cref="member">description</exception>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="16ea3-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="16ea3-109">See Also</span></span>  
 [<span data-ttu-id="16ea3-110">\<wyjątku ></span><span class="sxs-lookup"><span data-stu-id="16ea3-110">\<exception></span></span>](../../../visual-basic/language-reference/xmldoc/exception.md)  
 [<span data-ttu-id="16ea3-111">Porady: tworzenie dokumentacji XML</span><span class="sxs-lookup"><span data-stu-id="16ea3-111">How to: Create XML Documentation</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)  
 [<span data-ttu-id="16ea3-112">Tagi komentarza XML</span><span class="sxs-lookup"><span data-stu-id="16ea3-112">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)

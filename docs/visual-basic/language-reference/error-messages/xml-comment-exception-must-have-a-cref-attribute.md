---
title: Wyjątek komentarza XML musi mieć atrybut „cref”
ms.date: 07/20/2015
f1_keywords:
- bc42319
- vbc42319
helpviewer_keywords:
- BC42319
ms.assetid: 62eeeba3-6811-48be-b1ef-c2e4feda3177
ms.openlocfilehash: 2e57dc63cb7ad8b2e061296a082d6fa79b464f08
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/28/2019
ms.locfileid: "71592041"
---
# <a name="xml-comment-exception-must-have-a-cref-attribute"></a><span data-ttu-id="59c2e-102">Wyjątek komentarza XML musi mieć atrybut „cref”</span><span class="sxs-lookup"><span data-stu-id="59c2e-102">XML comment exception must have a 'cref' attribute</span></span>
<span data-ttu-id="59c2e-103">Tag \<exception > umożliwia dokumentowanie wyjątków, które mogą być zgłaszane przez metodę.</span><span class="sxs-lookup"><span data-stu-id="59c2e-103">The \<exception> tag provides a way to document the exceptions that may be thrown by a method.</span></span> <span data-ttu-id="59c2e-104">Wymagany atrybut `cref` Określa nazwę elementu członkowskiego, który jest sprawdzany przez generator dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="59c2e-104">The required `cref` attribute designates the name of a member, which is checked by the documentation generator.</span></span> <span data-ttu-id="59c2e-105">Jeśli element członkowski istnieje, jest tłumaczony na nazwę elementu kanonicznego w pliku dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="59c2e-105">If the member exists, it is translated to the canonical element name in the documentation file.</span></span>  
  
 <span data-ttu-id="59c2e-106">**Identyfikator błędu:** BC42319</span><span class="sxs-lookup"><span data-stu-id="59c2e-106">**Error ID:** BC42319</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="59c2e-107">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="59c2e-107">To correct this error</span></span>  
  
- <span data-ttu-id="59c2e-108">Dodaj atrybut `cref` do wyjątku w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="59c2e-108">Add the `cref` attribute to the exception as follows:</span></span>  
  
    <span data-ttu-id="59c2e-109">xml</span><span class="sxs-lookup"><span data-stu-id="59c2e-109">xml</span></span>  
    <span data-ttu-id="59c2e-110"><exception cref="member">Opis</exception> "" "</span><span class="sxs-lookup"><span data-stu-id="59c2e-110">'''<exception cref="member">description</exception></span></span>  
    ```  
  
## See also

- [\<exception>](../../../visual-basic/language-reference/xmldoc/exception.md)
- [How to: Create XML Documentation](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
- [XML Comment Tags](../../../visual-basic/language-reference/xmldoc/index.md)

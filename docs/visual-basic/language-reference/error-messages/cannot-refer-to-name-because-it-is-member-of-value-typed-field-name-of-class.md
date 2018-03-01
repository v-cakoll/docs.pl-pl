---
title: "Nie można odwołać się do &#39; &lt;nazwa&gt;&#39; ponieważ jest elementem członkowskim pola &#39;&lt; Nazwa&gt;&#39; klasa &#39;&lt; ClassName&gt;&#39; mającego &#39; System.MarshalByRefObject &#39; jako klasę podstawową"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30310
- bc30310
helpviewer_keywords:
- BC30310
ms.assetid: 2aeb8872-7c87-4f01-98ef-9714ba3eebbe
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7a84811b9f0e706cf3ebede09e07c03bd7e4cea4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="cannot-refer-to-39ltnamegt39-because-it-is-a-member-of-the-value-typed-field-39ltnamegt39-of-class-39ltclassnamegt39-which-has-39systemmarshalbyrefobject39-as-a-base-class"></a><span data-ttu-id="32846-102">Nie można odwołać się do &#39; &lt;nazwa&gt;&#39; ponieważ jest elementem członkowskim pola &#39;&lt; Nazwa&gt;&#39; klasa &#39;&lt; ClassName&gt;&#39; mającego &#39; System.MarshalByRefObject &#39; jako klasę podstawową</span><span class="sxs-lookup"><span data-stu-id="32846-102">Cannot refer to &#39;&lt;name&gt;&#39; because it is a member of the value-typed field &#39;&lt;name&gt;&#39; of class &#39;&lt;classname&gt;&#39; which has &#39;System.MarshalByRefObject&#39; as a base class</span></span>
<span data-ttu-id="32846-103">`System.MarshalByRefObject` Klasa umożliwia aplikacji, które obsługują zdalny dostęp do obiektów poza granice domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="32846-103">The `System.MarshalByRefObject` class enables applications that support remote access to objects across application domain boundaries.</span></span> <span data-ttu-id="32846-104">Typy musi dziedziczyć z `MarshalByRejectObject` klasy, gdy typ jest używany przez granice domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="32846-104">Types must inherit from the `MarshalByRejectObject` class when the type is used across application domain boundaries.</span></span> <span data-ttu-id="32846-105">Nie można skopiować stan obiektu, ponieważ w elementach członkowskich obiektu nie są użyteczne spoza domeny aplikacji, w którym zostały utworzone.</span><span class="sxs-lookup"><span data-stu-id="32846-105">The state of the object must not be copied because the members of the object are not usable outside the application domain in which they were created.</span></span>  
  
 <span data-ttu-id="32846-106">**Identyfikator błędu:** BC30310</span><span class="sxs-lookup"><span data-stu-id="32846-106">**Error ID:** BC30310</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="32846-107">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="32846-107">To correct this error</span></span>  
  
1.  <span data-ttu-id="32846-108">Sprawdź odwołania do upewnij się, że element członkowski jest określana jest prawidłowy.</span><span class="sxs-lookup"><span data-stu-id="32846-108">Check the reference to make sure the member being referred to is valid.</span></span>  
  
2.  <span data-ttu-id="32846-109">Jawnie zakwalifikować element członkowski o `Me` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="32846-109">Explicitly qualify the member with the `Me` keyword.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32846-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="32846-110">See Also</span></span>  
 <xref:System.MarshalByRefObject>  
 [<span data-ttu-id="32846-111">Dim — instrukcja</span><span class="sxs-lookup"><span data-stu-id="32846-111">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)

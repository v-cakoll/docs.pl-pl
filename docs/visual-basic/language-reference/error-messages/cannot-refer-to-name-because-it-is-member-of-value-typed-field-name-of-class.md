---
title: Nie można odwołać się &#39; &lt;nazwa&gt; &#39; , ponieważ jest to składowa pola &#39; &lt;nazwa&gt; &#39; klasy &#39; &lt;classname&gt; &#39;mającego &#39;System.MarshalByRefObject&#39; jako klasę bazową
ms.date: 07/20/2015
f1_keywords:
- vbc30310
- bc30310
helpviewer_keywords:
- BC30310
ms.assetid: 2aeb8872-7c87-4f01-98ef-9714ba3eebbe
ms.openlocfilehash: a6298c3e0f5102397d5cc3f237a186598c6b5ecc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54739300"
---
# <a name="cannot-refer-to-39ltnamegt39-because-it-is-a-member-of-the-value-typed-field-39ltnamegt39-of-class-39ltclassnamegt39-which-has-39systemmarshalbyrefobject39-as-a-base-class"></a><span data-ttu-id="2541e-102">Nie można odwołać się &#39; &lt;nazwa&gt; &#39; , ponieważ jest to składowa pola &#39; &lt;nazwa&gt; &#39; klasy &#39; &lt;classname&gt; &#39;mającego &#39;System.MarshalByRefObject&#39; jako klasę bazową</span><span class="sxs-lookup"><span data-stu-id="2541e-102">Cannot refer to &#39;&lt;name&gt;&#39; because it is a member of the value-typed field &#39;&lt;name&gt;&#39; of class &#39;&lt;classname&gt;&#39; which has &#39;System.MarshalByRefObject&#39; as a base class</span></span>
<span data-ttu-id="2541e-103">`System.MarshalByRefObject` Klasa umożliwia aplikacji, które obsługują zdalny dostęp do obiektów poza granice domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="2541e-103">The `System.MarshalByRefObject` class enables applications that support remote access to objects across application domain boundaries.</span></span> <span data-ttu-id="2541e-104">Typy musi dziedziczyć `MarshalByRejectObject` klasy, gdy typ jest używany poza granice domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="2541e-104">Types must inherit from the `MarshalByRejectObject` class when the type is used across application domain boundaries.</span></span> <span data-ttu-id="2541e-105">Nie można skopiować stan obiektu, ponieważ elementy członkowskie obiektu nie są użyteczne spoza domeny aplikacji, w którym zostały utworzone.</span><span class="sxs-lookup"><span data-stu-id="2541e-105">The state of the object must not be copied because the members of the object are not usable outside the application domain in which they were created.</span></span>  
  
 <span data-ttu-id="2541e-106">**Identyfikator błędu:** BC30310</span><span class="sxs-lookup"><span data-stu-id="2541e-106">**Error ID:** BC30310</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="2541e-107">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="2541e-107">To correct this error</span></span>  
  
1.  <span data-ttu-id="2541e-108">Sprawdzanie odwołania, aby upewnić się, że przywoływanego elementu członkowskiego jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="2541e-108">Check the reference to make sure the member being referred to is valid.</span></span>  
  
2.  <span data-ttu-id="2541e-109">Kwalifikuj jawnie elementu członkowskiego z `Me` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="2541e-109">Explicitly qualify the member with the `Me` keyword.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2541e-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2541e-110">See also</span></span>
- <xref:System.MarshalByRefObject>
- [<span data-ttu-id="2541e-111">Dim, instrukcja</span><span class="sxs-lookup"><span data-stu-id="2541e-111">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)

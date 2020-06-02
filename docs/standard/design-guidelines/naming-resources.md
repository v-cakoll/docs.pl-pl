---
title: Nazewnictwo zasobów
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- names [.NET Framework], localized resources
- localization, naming guidelines
- resource names
- global applications, naming guidelines
- international applications, naming guidelines
ms.assetid: 8b0e97f3-7877-44fd-bc76-e05d36d5d79c
ms.openlocfilehash: 762ba99c4751ba40f5f33e99455cf950af35cdf6
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290152"
---
# <a name="naming-resources"></a><span data-ttu-id="d0f94-102">Nazewnictwo zasobów</span><span class="sxs-lookup"><span data-stu-id="d0f94-102">Naming Resources</span></span>
<span data-ttu-id="d0f94-103">Ponieważ zasoby lokalizowalne mogą być przywoływane za pośrednictwem pewnych obiektów, tak jakby były właściwościami, wskazówki dotyczące nazewnictwa dla zasobów są podobne do wytycznych dotyczących właściwości.</span><span class="sxs-lookup"><span data-stu-id="d0f94-103">Because localizable resources can be referenced via certain objects as if they were properties, the naming guidelines for resources are similar to property guidelines.</span></span>

 <span data-ttu-id="d0f94-104">✔️ używać PascalCasing w kluczach zasobów.</span><span class="sxs-lookup"><span data-stu-id="d0f94-104">✔️ DO use PascalCasing in resource keys.</span></span>

 <span data-ttu-id="d0f94-105">✔️ Podaj opis, a nie krótkie identyfikatory.</span><span class="sxs-lookup"><span data-stu-id="d0f94-105">✔️ DO provide descriptive rather than short identifiers.</span></span>

 <span data-ttu-id="d0f94-106">❌NIE używaj słów kluczowych właściwych dla języka dla głównych języków CLR.</span><span class="sxs-lookup"><span data-stu-id="d0f94-106">❌ DO NOT use language-specific keywords of the main CLR languages.</span></span>

 <span data-ttu-id="d0f94-107">✔️ używać tylko znaków alfanumerycznych i podkreśleń w przypadku nazw zasobów.</span><span class="sxs-lookup"><span data-stu-id="d0f94-107">✔️ DO use only alphanumeric characters and underscores in naming resources.</span></span>

 <span data-ttu-id="d0f94-108">✔️ używać następującej konwencji nazewnictwa dla zasobów komunikatów o wyjątkach.</span><span class="sxs-lookup"><span data-stu-id="d0f94-108">✔️ DO use the following naming convention for exception message resources.</span></span>

 <span data-ttu-id="d0f94-109">Identyfikator zasobu powinien być nazwą typu wyjątku i krótkim identyfikatorem wyjątku:</span><span class="sxs-lookup"><span data-stu-id="d0f94-109">The resource identifier should be the exception type name plus a short identifier of the exception:</span></span>

 <span data-ttu-id="d0f94-110">`ArgumentExceptionIllegalCharacters` `ArgumentExceptionInvalidName`</span><span class="sxs-lookup"><span data-stu-id="d0f94-110">`ArgumentExceptionIllegalCharacters` `ArgumentExceptionInvalidName`</span></span>
 `ArgumentExceptionFileNameIsMalformed`

 <span data-ttu-id="d0f94-111">*Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="d0f94-111">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="d0f94-112">*Ponownie Wydrukowano przez uprawnienie Pearson Education, Inc. z [wytycznych dotyczących projektowania platformy: konwencje, idiomy i wzorce dla bibliotek .NET do wielokrotnego użytku, 2. wydanie](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) przez Krzysztof Cwalina i Brad Abrams, opublikowane 22, 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development.*</span><span class="sxs-lookup"><span data-stu-id="d0f94-112">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="d0f94-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d0f94-113">See also</span></span>

- [<span data-ttu-id="d0f94-114">Wskazówki dotyczące projektowania struktury</span><span class="sxs-lookup"><span data-stu-id="d0f94-114">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="d0f94-115">Wskazówki dotyczące nazewnictwa</span><span class="sxs-lookup"><span data-stu-id="d0f94-115">Naming Guidelines</span></span>](naming-guidelines.md)

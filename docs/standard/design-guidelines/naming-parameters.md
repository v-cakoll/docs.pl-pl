---
title: Nazewnictwo parametrów
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- parameters, names
- names [.NET Framework], parameters
ms.assetid: ca3c956e-725a-441b-b4e3-eab5d472f41c
ms.openlocfilehash: 0d5c5cd144fbae88439ee981fbdb6e30ff487005
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290165"
---
# <a name="naming-parameters"></a><span data-ttu-id="af9de-102">Nazewnictwo parametrów</span><span class="sxs-lookup"><span data-stu-id="af9de-102">Naming Parameters</span></span>
<span data-ttu-id="af9de-103">Poza oczywistym powodem czytelności należy postępować zgodnie z wytycznymi dotyczącymi nazw parametrów, ponieważ parametry są wyświetlane w dokumentacji i w projektancie, gdy narzędzia projektowania wizualnego zapewniają funkcje IntelliSense i przeglądanie klas.</span><span class="sxs-lookup"><span data-stu-id="af9de-103">Beyond the obvious reason of readability, it is important to follow the guidelines for parameter names because parameters are displayed in documentation and in the designer when visual design tools provide Intellisense and class browsing functionality.</span></span>

 <span data-ttu-id="af9de-104">✔️ używać camelCasing w nazwach parametrów.</span><span class="sxs-lookup"><span data-stu-id="af9de-104">✔️ DO use camelCasing in parameter names.</span></span>

 <span data-ttu-id="af9de-105">✔️ należy używać opisowych nazw parametrów.</span><span class="sxs-lookup"><span data-stu-id="af9de-105">✔️ DO use descriptive parameter names.</span></span>

 <span data-ttu-id="af9de-106">✔️ ROZWAŻYĆ użycie nazw na podstawie znaczenia parametru, a nie typu parametru.</span><span class="sxs-lookup"><span data-stu-id="af9de-106">✔️ CONSIDER using names based on a parameter’s meaning rather than the parameter’s type.</span></span>

### <a name="naming-operator-overload-parameters"></a><span data-ttu-id="af9de-107">Parametry przeciążenia operatora nazewnictwa</span><span class="sxs-lookup"><span data-stu-id="af9de-107">Naming Operator Overload Parameters</span></span>
 <span data-ttu-id="af9de-108">✔️ Użyj `left` i `right` dla nazw parametrów przeciążenia operatora binarnego, jeśli nie ma znaczenia dla parametrów.</span><span class="sxs-lookup"><span data-stu-id="af9de-108">✔️ DO use `left` and `right` for binary operator overload parameter names if there is no meaning to the parameters.</span></span>

 <span data-ttu-id="af9de-109">✔️ używać `value` dla jednoargumentowych nazw parametrów przeciążenia, jeśli nie ma znaczenia dla parametrów.</span><span class="sxs-lookup"><span data-stu-id="af9de-109">✔️ DO use `value` for unary operator overload parameter names if there is no meaning to the parameters.</span></span>

 <span data-ttu-id="af9de-110">✔️ NALEŻY rozważyć znaczące nazwy dla parametrów przeciążenia operatora, jeśli spowoduje to dodanie znaczącej wartości.</span><span class="sxs-lookup"><span data-stu-id="af9de-110">✔️ CONSIDER meaningful names for operator overload parameters if doing so adds significant value.</span></span>

 <span data-ttu-id="af9de-111">❌NIE używaj skrótów ani indeksów liczbowych dla nazw parametrów przeciążenia operatora.</span><span class="sxs-lookup"><span data-stu-id="af9de-111">❌ DO NOT use abbreviations or numeric indices for operator overload parameter names.</span></span>

 <span data-ttu-id="af9de-112">*Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="af9de-112">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="af9de-113">*Ponownie Wydrukowano przez uprawnienie Pearson Education, Inc. z [wytycznych dotyczących projektowania platformy: konwencje, idiomy i wzorce dla bibliotek .NET do wielokrotnego użytku, 2. wydanie](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) przez Krzysztof Cwalina i Brad Abrams, opublikowane 22, 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development.*</span><span class="sxs-lookup"><span data-stu-id="af9de-113">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="af9de-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="af9de-114">See also</span></span>

- [<span data-ttu-id="af9de-115">Wskazówki dotyczące projektowania struktury</span><span class="sxs-lookup"><span data-stu-id="af9de-115">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="af9de-116">Wskazówki dotyczące nazewnictwa</span><span class="sxs-lookup"><span data-stu-id="af9de-116">Naming Guidelines</span></span>](naming-guidelines.md)

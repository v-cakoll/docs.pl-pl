---
title: Nazewnictwo parametrów
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- parameters, names
- names [.NET Framework], parameters
ms.assetid: ca3c956e-725a-441b-b4e3-eab5d472f41c
ms.openlocfilehash: ebe2e2db4b109057bf576d4e18cfe511c657707e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743829"
---
# <a name="naming-parameters"></a><span data-ttu-id="36ecf-102">Nazewnictwo parametrów</span><span class="sxs-lookup"><span data-stu-id="36ecf-102">Naming Parameters</span></span>
<span data-ttu-id="36ecf-103">Poza oczywistym powodem czytelności należy postępować zgodnie z wytycznymi dotyczącymi nazw parametrów, ponieważ parametry są wyświetlane w dokumentacji i w projektancie, gdy narzędzia projektowania wizualnego zapewniają funkcje IntelliSense i przeglądanie klas.</span><span class="sxs-lookup"><span data-stu-id="36ecf-103">Beyond the obvious reason of readability, it is important to follow the guidelines for parameter names because parameters are displayed in documentation and in the designer when visual design tools provide Intellisense and class browsing functionality.</span></span>

 <span data-ttu-id="36ecf-104">✔️ używać camelCasing w nazwach parametrów.</span><span class="sxs-lookup"><span data-stu-id="36ecf-104">✔️ DO use camelCasing in parameter names.</span></span>

 <span data-ttu-id="36ecf-105">✔️ należy używać opisowych nazw parametrów.</span><span class="sxs-lookup"><span data-stu-id="36ecf-105">✔️ DO use descriptive parameter names.</span></span>

 <span data-ttu-id="36ecf-106">✔️ ROZWAŻYĆ użycie nazw na podstawie znaczenia parametru, a nie typu parametru.</span><span class="sxs-lookup"><span data-stu-id="36ecf-106">✔️ CONSIDER using names based on a parameter’s meaning rather than the parameter’s type.</span></span>

### <a name="naming-operator-overload-parameters"></a><span data-ttu-id="36ecf-107">Parametry przeciążenia operatora nazewnictwa</span><span class="sxs-lookup"><span data-stu-id="36ecf-107">Naming Operator Overload Parameters</span></span>
 <span data-ttu-id="36ecf-108">✔️ używać `left` i `right` dla nazw parametrów przeciążenia operatora binarnego, jeśli nie ma znaczenia dla parametrów.</span><span class="sxs-lookup"><span data-stu-id="36ecf-108">✔️ DO use `left` and `right` for binary operator overload parameter names if there is no meaning to the parameters.</span></span>

 <span data-ttu-id="36ecf-109">✔️ używać `value` dla nazw parametrów przeciążenia operatora jednoargumentowego, jeśli nie ma znaczenia dla parametrów.</span><span class="sxs-lookup"><span data-stu-id="36ecf-109">✔️ DO use `value` for unary operator overload parameter names if there is no meaning to the parameters.</span></span>

 <span data-ttu-id="36ecf-110">✔️ NALEŻY rozważyć znaczące nazwy dla parametrów przeciążenia operatora, jeśli spowoduje to dodanie znaczącej wartości.</span><span class="sxs-lookup"><span data-stu-id="36ecf-110">✔️ CONSIDER meaningful names for operator overload parameters if doing so adds significant value.</span></span>

 <span data-ttu-id="36ecf-111">❌ nie używaj skrótów ani indeksów liczbowych dla nazw parametrów przeciążenia operatora.</span><span class="sxs-lookup"><span data-stu-id="36ecf-111">❌ DO NOT use abbreviations or numeric indices for operator overload parameter names.</span></span>

 <span data-ttu-id="36ecf-112">*Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="36ecf-112">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="36ecf-113">*Ponownie Wydrukowano przez uprawnienie Pearson Education, Inc. z [wytycznych dotyczących projektowania platformy: konwencje, idiomy i wzorce dla bibliotek .NET do wielokrotnego użytku, 2. wydanie](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) przez Krzysztof Cwalina i Brad Abrams, opublikowane 22, 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development.*</span><span class="sxs-lookup"><span data-stu-id="36ecf-113">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="36ecf-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="36ecf-114">See also</span></span>

- [<span data-ttu-id="36ecf-115">Struktura — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="36ecf-115">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="36ecf-116">Wskazówki dotyczące nazewnictwa</span><span class="sxs-lookup"><span data-stu-id="36ecf-116">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)

---
title: Nazewnictwo parametrów
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- parameters, names
- names [.NET Framework], parameters
ms.assetid: ca3c956e-725a-441b-b4e3-eab5d472f41c
author: KrzysztofCwalina
ms.openlocfilehash: 0e5b33839372e303b96bd6b84949f9a82da2f689
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54646623"
---
# <a name="naming-parameters"></a><span data-ttu-id="c7aa6-102">Nazewnictwo parametrów</span><span class="sxs-lookup"><span data-stu-id="c7aa6-102">Naming Parameters</span></span>
<span data-ttu-id="c7aa6-103">Poza oczywiste powodu czytelności warto postępuj zgodnie z wytycznymi dla nazw parametrów, ponieważ parametry są wyświetlane w dokumentacji i w projektancie, gdy zawierają narzędzi do projektowania wizualnego, funkcja Intellisense i przeglądania funkcji klasy.</span><span class="sxs-lookup"><span data-stu-id="c7aa6-103">Beyond the obvious reason of readability, it is important to follow the guidelines for parameter names because parameters are displayed in documentation and in the designer when visual design tools provide Intellisense and class browsing functionality.</span></span>  
  
 <span data-ttu-id="c7aa6-104">**✓ DO** Użyj camelCasing w nazwach parametrów.</span><span class="sxs-lookup"><span data-stu-id="c7aa6-104">**✓ DO** use camelCasing in parameter names.</span></span>  
  
 <span data-ttu-id="c7aa6-105">**✓ DO** Użyj nazwy opisowej parametrów.</span><span class="sxs-lookup"><span data-stu-id="c7aa6-105">**✓ DO** use descriptive parameter names.</span></span>  
  
 <span data-ttu-id="c7aa6-106">**✓ CONSIDER** przy użyciu nazwy parametru znaczenie niż typ parametru.</span><span class="sxs-lookup"><span data-stu-id="c7aa6-106">**✓ CONSIDER** using names based on a parameter’s meaning rather than the parameter’s type.</span></span>  
  
### <a name="naming-operator-overload-parameters"></a><span data-ttu-id="c7aa6-107">Nazywanie parametrów przeciążenia operatora</span><span class="sxs-lookup"><span data-stu-id="c7aa6-107">Naming Operator Overload Parameters</span></span>  
 <span data-ttu-id="c7aa6-108">**✓ DO** użyj `left` i `right` dla nazw parametrów przeciążenia operatora binarnego Jeśli znaczenia parametrów nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="c7aa6-108">**✓ DO** use `left` and `right` for binary operator overload parameter names if there is no meaning to the parameters.</span></span>  
  
 <span data-ttu-id="c7aa6-109">**✓ DO** użyj `value` dla Jednoargumentowy operator przeciążenia nazwy parametrów, jeśli żadnego znaczenia parametrów nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="c7aa6-109">**✓ DO** use `value` for unary operator overload parameter names if there is no meaning to the parameters.</span></span>  
  
 <span data-ttu-id="c7aa6-110">**✓ CONSIDER** łatwy do rozpoznania nazwy dla operatora przeciążenia parametrów, jeśli wykonanie tej tak dodaje wartość.</span><span class="sxs-lookup"><span data-stu-id="c7aa6-110">**✓ CONSIDER** meaningful names for operator overload parameters if doing so adds significant value.</span></span>  
  
 <span data-ttu-id="c7aa6-111">**X DO NOT** Użyj skrótów lub wskaźniki liczbowe dla operatora przeciążenia nazwy parametrów.</span><span class="sxs-lookup"><span data-stu-id="c7aa6-111">**X DO NOT** use abbreviations or numeric indices for operator overload parameter names.</span></span>  
  
 <span data-ttu-id="c7aa6-112">*Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="c7aa6-112">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="c7aa6-113">*Przedrukowano za uprawnienie Pearson edukacji, Inc. z [wytyczne dotyczące projektowania Framework: Konwencje, Idiomy i wzorców dla wielokrotnego użytku, do bibliotek .NET, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Brad Abrams publikowane 22 Oct 2008 przez Addison Wesley Professional w ramach serii rozwoju Windows firmy Microsoft.*</span><span class="sxs-lookup"><span data-stu-id="c7aa6-113">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7aa6-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c7aa6-114">See also</span></span>

- [<span data-ttu-id="c7aa6-115">Struktura — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="c7aa6-115">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="c7aa6-116">Wskazówki dotyczące nazewnictwa</span><span class="sxs-lookup"><span data-stu-id="c7aa6-116">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)

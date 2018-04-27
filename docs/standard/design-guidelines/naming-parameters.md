---
title: Nazwy parametrów
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- parameters, names
- names [.NET Framework], parameters
ms.assetid: ca3c956e-725a-441b-b4e3-eab5d472f41c
caps.latest.revision: 9
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 3e5dfe35fd4f2939898acee44764535c6de5fe9e
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="naming-parameters"></a><span data-ttu-id="f6d85-102">Nazwy parametrów</span><span class="sxs-lookup"><span data-stu-id="f6d85-102">Naming Parameters</span></span>
<span data-ttu-id="f6d85-103">Poza oczywiste Przyczyna czytelności koniecznie postępuj zgodnie z wytycznymi dla nazw parametrów, ponieważ parametry są wyświetlane w dokumentacji i w projektancie, podając Intellisense i przeglądania funkcje klasy narzędzi do projektowania visual.</span><span class="sxs-lookup"><span data-stu-id="f6d85-103">Beyond the obvious reason of readability, it is important to follow the guidelines for parameter names because parameters are displayed in documentation and in the designer when visual design tools provide Intellisense and class browsing functionality.</span></span>  
  
 <span data-ttu-id="f6d85-104">**CZY ✓** Użyj camelCasing w nazwach parametrów.</span><span class="sxs-lookup"><span data-stu-id="f6d85-104">**✓ DO** use camelCasing in parameter names.</span></span>  
  
 <span data-ttu-id="f6d85-105">**CZY ✓** Użyj nazwy opisowej parametrów.</span><span class="sxs-lookup"><span data-stu-id="f6d85-105">**✓ DO** use descriptive parameter names.</span></span>  
  
 <span data-ttu-id="f6d85-106">**ROZWAŻ ✓** przy użyciu nazwy parametru znaczenie niż typ parametru.</span><span class="sxs-lookup"><span data-stu-id="f6d85-106">**✓ CONSIDER** using names based on a parameter’s meaning rather than the parameter’s type.</span></span>  
  
### <a name="naming-operator-overload-parameters"></a><span data-ttu-id="f6d85-107">Nazwy parametrów przeciążenia operatora</span><span class="sxs-lookup"><span data-stu-id="f6d85-107">Naming Operator Overload Parameters</span></span>  
 <span data-ttu-id="f6d85-108">**CZY ✓** użyj `left` i `right` dla nazw parametrów przeciążenia operatora binarnego Jeśli znaczenia parametrów nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="f6d85-108">**✓ DO** use `left` and `right` for binary operator overload parameter names if there is no meaning to the parameters.</span></span>  
  
 <span data-ttu-id="f6d85-109">**CZY ✓** użyj `value` dla Jednoargumentowy operator przeciążenia nazwy parametrów, jeśli żadnego znaczenia parametrów nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="f6d85-109">**✓ DO** use `value` for unary operator overload parameter names if there is no meaning to the parameters.</span></span>  
  
 <span data-ttu-id="f6d85-110">**ROZWAŻ ✓** łatwy do rozpoznania nazwy dla operatora przeciążenia parametrów, jeśli wykonanie tej tak dodaje wartość.</span><span class="sxs-lookup"><span data-stu-id="f6d85-110">**✓ CONSIDER** meaningful names for operator overload parameters if doing so adds significant value.</span></span>  
  
 <span data-ttu-id="f6d85-111">**X nie** Użyj skrótów lub wskaźniki liczbowe dla operatora przeciążenia nazwy parametrów.</span><span class="sxs-lookup"><span data-stu-id="f6d85-111">**X DO NOT** use abbreviations or numeric indices for operator overload parameter names.</span></span>  
  
 <span data-ttu-id="f6d85-112">*Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="f6d85-112">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="f6d85-113">*Drukowane uprawnieniami wariancji x edukacji, Inc. z [Framework zaleceń dotyczących projektowania: konwencje, Idioms i wzorce dla bibliotek .NET wielokrotnego użytku, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Abrams Brada opublikowane 22 Oct 2008 przez Professional Addison-Wesley jako część serii rozwoju systemu Windows firmy Microsoft.*</span><span class="sxs-lookup"><span data-stu-id="f6d85-113">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6d85-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f6d85-114">See Also</span></span>  
 [<span data-ttu-id="f6d85-115">Struktura — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="f6d85-115">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="f6d85-116">Wskazówki dotyczące nazewnictwa</span><span class="sxs-lookup"><span data-stu-id="f6d85-116">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)

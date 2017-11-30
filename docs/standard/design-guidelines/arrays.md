---
title: Tablice
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- class library design guidelines [.NET Framework], arrays
- arrays [.NET Framework], usage guidelines
- empty arrays
ms.assetid: 66a1b3d8-6f3f-4715-b235-e1ff95e32d8e
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c957d4336527de8c11b763c31c1fdf0015b675b6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="arrays"></a><span data-ttu-id="9be62-102">Tablice</span><span class="sxs-lookup"><span data-stu-id="9be62-102">Arrays</span></span>
<span data-ttu-id="9be62-103">**CZY ✓** preferowane przy użyciu kolekcji za pośrednictwem tablic w publicznych interfejsach API.</span><span class="sxs-lookup"><span data-stu-id="9be62-103">**✓ DO** prefer using collections over arrays in public APIs.</span></span> <span data-ttu-id="9be62-104">[Kolekcje](../../../docs/standard/design-guidelines/guidelines-for-collections.md) sekcja zawiera szczegółowe informacje o tym, jak wybranie kolekcji i tablic.</span><span class="sxs-lookup"><span data-stu-id="9be62-104">The [Collections](../../../docs/standard/design-guidelines/guidelines-for-collections.md) section provides details about how to choose between collections and arrays.</span></span>  
  
 <span data-ttu-id="9be62-105">**X nie** użyć pola tablicy tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="9be62-105">**X DO NOT** use read-only array fields.</span></span> <span data-ttu-id="9be62-106">Samo pole jest tylko do odczytu i nie można zmienić, ale można zmienić elementów w tablicy.</span><span class="sxs-lookup"><span data-stu-id="9be62-106">The field itself is read-only and can't be changed, but elements in the array can be changed.</span></span>  
  
 <span data-ttu-id="9be62-107">**ROZWAŻ ✓** za pomocą Tablice nieregularne zamiast wielowymiarowych tablic.</span><span class="sxs-lookup"><span data-stu-id="9be62-107">**✓ CONSIDER** using jagged arrays instead of multidimensional arrays.</span></span>  
  
 <span data-ttu-id="9be62-108">Nieregularna tablica jest tablicą z elementami, które są również tablic.</span><span class="sxs-lookup"><span data-stu-id="9be62-108">A jagged array is an array with elements that are also arrays.</span></span> <span data-ttu-id="9be62-109">Tablice, które tworzą elementów może mieć różne rozmiary, co może prowadzić do mniej utracona dla niektórych zestawów danych (np. macierz rozrzedzone) w porównaniu do tablic wielowymiarowych.</span><span class="sxs-lookup"><span data-stu-id="9be62-109">The arrays that make up the elements can be of different sizes, leading to less wasted space for some sets of data (e.g., sparse matrix) compared to multidimensional arrays.</span></span> <span data-ttu-id="9be62-110">Ponadto CLR optymalizuje operacje na indeksie na Tablice nieregularne tak może charakteryzują się lepszą wydajność środowiska uruchomieniowego w niektórych scenariuszach.</span><span class="sxs-lookup"><span data-stu-id="9be62-110">Furthermore, the CLR optimizes index operations on jagged arrays, so they might exhibit better runtime performance in some scenarios.</span></span>  
  
 <span data-ttu-id="9be62-111">*Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="9be62-111">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="9be62-112">*Drukowane uprawnieniami wariancji x edukacji, Inc. z [Framework zaleceń dotyczących projektowania: konwencje, Idioms i wzorce dla bibliotek .NET wielokrotnego użytku, wydanie 2](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Abrams Brada opublikowane 22 Oct 2008 przez Professional Addison-Wesley jako część serii rozwoju systemu Windows firmy Microsoft.*</span><span class="sxs-lookup"><span data-stu-id="9be62-112">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9be62-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9be62-113">See Also</span></span>  
 <xref:System.Array>  
 [<span data-ttu-id="9be62-114">Wytyczne dotyczące projektowania Framework</span><span class="sxs-lookup"><span data-stu-id="9be62-114">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="9be62-115">Wskazówki dotyczące użycia</span><span class="sxs-lookup"><span data-stu-id="9be62-115">Usage Guidelines</span></span>](../../../docs/standard/design-guidelines/usage-guidelines.md)

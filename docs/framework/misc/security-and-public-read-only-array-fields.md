---
title: Bezpieczeństwo i publiczne pola tablicy tylko do odczytu
description: Przeczytaj, dlaczego należy unikać używania publicznych pól tablicy tylko do odczytu, aby zdefiniować zachowanie granicy lub bezpieczeństwo aplikacji.
ms.date: 03/30/2017
helpviewer_keywords:
- security [.NET Framework], public read-only array fields
ms.assetid: 3df28dee-2a9f-40ff-9852-bfdbe59c27f3
ms.openlocfilehash: 0a6a82c2c88fe61bd34c0accb831f018cf8702fc
ms.sourcegitcommit: 97ce5363efa88179dd76e09de0103a500ca9b659
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/13/2020
ms.locfileid: "86281436"
---
# <a name="security-and-public-read-only-array-fields"></a><span data-ttu-id="6f71e-103">Bezpieczeństwo i publiczne pola tablicy tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="6f71e-103">Security and Public Read-only Array Fields</span></span>
<span data-ttu-id="6f71e-104">Nie używaj pól tablicy publicznej tylko do odczytu z bibliotek zarządzanych, aby zdefiniować zachowanie granic lub zabezpieczenia aplikacji, ponieważ można modyfikować pola tablicy publicznej tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="6f71e-104">Never use read-only public array fields from managed libraries to define the boundary behavior or security of your applications because read-only public array fields can be modified.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6f71e-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6f71e-105">Remarks</span></span>  

<span data-ttu-id="6f71e-106">Niektóre klasy .NET zawierają pola publiczne tylko do odczytu, które zawierają parametry graniczne specyficzne dla platformy.</span><span class="sxs-lookup"><span data-stu-id="6f71e-106">Some .NET classes include read-only public fields that contain platform-specific boundary parameters.</span></span> <span data-ttu-id="6f71e-107">Na przykład <xref:System.IO.Path.InvalidPathChars> pole jest tablicą opisującą znaki, które nie są dozwolone w ciągu ścieżki do pliku.</span><span class="sxs-lookup"><span data-stu-id="6f71e-107">For example, the <xref:System.IO.Path.InvalidPathChars> field is an array that describes the characters that are not allowed in a file path string.</span></span> <span data-ttu-id="6f71e-108">W środowisku .NET są obecne wiele podobnych pól.</span><span class="sxs-lookup"><span data-stu-id="6f71e-108">Many similar fields are present throughout .NET.</span></span>  
  
 <span data-ttu-id="6f71e-109">Wartości publicznych pól tylko do odczytu, takich jak <xref:System.IO.Path.InvalidPathChars> mogą być modyfikowane przez kod lub kod, który współużytkują domenę aplikacji kodu.</span><span class="sxs-lookup"><span data-stu-id="6f71e-109">The values of public read-only fields like <xref:System.IO.Path.InvalidPathChars> can be modified by your code or code that shares your code’s application domain.</span></span>  <span data-ttu-id="6f71e-110">Nie należy używać pól tablic publicznych tylko do odczytu, takich jak to, aby zdefiniować zachowanie granic aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6f71e-110">You should not use read-only public array fields like this to define the boundary behavior of your applications.</span></span>  <span data-ttu-id="6f71e-111">Jeśli to zrobisz, złośliwy kod może zmienić definicje granic i użyć kodu w nieoczekiwany sposób.</span><span class="sxs-lookup"><span data-stu-id="6f71e-111">If you do, malicious code can alter the boundary definitions and use your code in unexpected ways.</span></span>  
  
 <span data-ttu-id="6f71e-112">W wersji 2,0 i nowszych .NET Framework należy używać metod, które zwracają nową tablicę zamiast używać publicznych pól tablic.</span><span class="sxs-lookup"><span data-stu-id="6f71e-112">In version 2.0 and later of the .NET Framework, you should use methods that return a new array instead of using public array fields.</span></span>  <span data-ttu-id="6f71e-113">Na przykład zamiast używać <xref:System.IO.Path.InvalidPathChars> pola, należy użyć <xref:System.IO.Path.GetInvalidPathChars%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="6f71e-113">For example, instead of using the <xref:System.IO.Path.InvalidPathChars> field, you should use the <xref:System.IO.Path.GetInvalidPathChars%2A> method.</span></span>  
  
 <span data-ttu-id="6f71e-114">Należy zauważyć, że typy .NET Framework nie używają publicznych pól do wewnętrznego definiowania typów granic.</span><span class="sxs-lookup"><span data-stu-id="6f71e-114">Note that the .NET Framework types do not use the public fields to define boundary types internally.</span></span>  <span data-ttu-id="6f71e-115">Zamiast tego .NET Framework używa oddzielnych pól prywatnych.</span><span class="sxs-lookup"><span data-stu-id="6f71e-115">Instead, the .NET Framework uses separate private fields.</span></span>  <span data-ttu-id="6f71e-116">Zmiana wartości tych pól publicznych nie powoduje zmiany zachowania typów .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6f71e-116">Changing the values of these public fields does not alter the behavior of .NET Framework types.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f71e-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6f71e-117">See also</span></span>

- [<span data-ttu-id="6f71e-118">Wytyczne dotyczące bezpiecznego programowania</span><span class="sxs-lookup"><span data-stu-id="6f71e-118">Secure Coding Guidelines</span></span>](../../standard/security/secure-coding-guidelines.md)

---
title: Bezpieczeństwo i publiczne pola tablicy tylko do odczytu
ms.date: 03/30/2017
helpviewer_keywords:
- security [.NET Framework], public read-only array fields
ms.assetid: 3df28dee-2a9f-40ff-9852-bfdbe59c27f3
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3d36009fa4fc7b9299708768fe34a75f1fde6797
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69910734"
---
# <a name="security-and-public-read-only-array-fields"></a><span data-ttu-id="e07ee-102">Bezpieczeństwo i publiczne pola tablicy tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="e07ee-102">Security and Public Read-only Array Fields</span></span>
<span data-ttu-id="e07ee-103">Nie używaj pól tablicy publicznej tylko do odczytu z bibliotek zarządzanych, aby zdefiniować zachowanie granic lub zabezpieczenia aplikacji, ponieważ można modyfikować pola tablicy publicznej tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="e07ee-103">Never use read-only public array fields from managed libraries to define the boundary behavior or security of your applications because read-only public array fields can be modified.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e07ee-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e07ee-104">Remarks</span></span>  
 <span data-ttu-id="e07ee-105">Niektóre klasy .NET Framework zawierają pola publiczne tylko do odczytu, które zawierają parametry graniczne specyficzne dla platformy.</span><span class="sxs-lookup"><span data-stu-id="e07ee-105">Some .NET framework classes include read-only public fields that contain platform-specific boundary parameters.</span></span>  <span data-ttu-id="e07ee-106">Na przykład <xref:System.IO.Path.InvalidPathChars> pole jest tablicą opisującą znaki, które nie są dozwolone w ciągu ścieżki do pliku.</span><span class="sxs-lookup"><span data-stu-id="e07ee-106">For example, the <xref:System.IO.Path.InvalidPathChars> field is an array that describes the characters that are not allowed in a file path string.</span></span>  <span data-ttu-id="e07ee-107">W .NET Framework są obecne wiele podobnych pól.</span><span class="sxs-lookup"><span data-stu-id="e07ee-107">Many similar fields are present throughout the .NET Framework.</span></span>  
  
 <span data-ttu-id="e07ee-108">Wartości publicznych pól tylko do odczytu, takich jak <xref:System.IO.Path.InvalidPathChars> mogą być modyfikowane przez kod lub kod, który współużytkują domenę aplikacji kodu.</span><span class="sxs-lookup"><span data-stu-id="e07ee-108">The values of public read-only fields like <xref:System.IO.Path.InvalidPathChars> can be modified by your code or code that shares your code’s application domain.</span></span>  <span data-ttu-id="e07ee-109">Nie należy używać pól tablic publicznych tylko do odczytu, takich jak to, aby zdefiniować zachowanie granic aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e07ee-109">You should not use read-only public array fields like this to define the boundary behavior of your applications.</span></span>  <span data-ttu-id="e07ee-110">Jeśli to zrobisz, złośliwy kod może zmienić definicje granic i użyć kodu w nieoczekiwany sposób.</span><span class="sxs-lookup"><span data-stu-id="e07ee-110">If you do, malicious code can alter the boundary definitions and use your code in unexpected ways.</span></span>  
  
 <span data-ttu-id="e07ee-111">W wersji 2,0 i nowszych .NET Framework należy używać metod, które zwracają nową tablicę zamiast używać publicznych pól tablic.</span><span class="sxs-lookup"><span data-stu-id="e07ee-111">In version 2.0 and later of the .NET Framework, you should use methods that return a new array instead of using public array fields.</span></span>  <span data-ttu-id="e07ee-112">Na przykład zamiast używać <xref:System.IO.Path.InvalidPathChars> pola, należy <xref:System.IO.Path.GetInvalidPathChars%2A> użyć metody.</span><span class="sxs-lookup"><span data-stu-id="e07ee-112">For example, instead of using the <xref:System.IO.Path.InvalidPathChars> field, you should use the <xref:System.IO.Path.GetInvalidPathChars%2A> method.</span></span>  
  
 <span data-ttu-id="e07ee-113">Należy zauważyć, że typy .NET Framework nie używają publicznych pól do wewnętrznego definiowania typów granic.</span><span class="sxs-lookup"><span data-stu-id="e07ee-113">Note that the .NET Framework types do not use the public fields to define boundary types internally.</span></span>  <span data-ttu-id="e07ee-114">Zamiast tego .NET Framework używa oddzielnych pól prywatnych.</span><span class="sxs-lookup"><span data-stu-id="e07ee-114">Instead, the .NET Framework uses separate private fields.</span></span>  <span data-ttu-id="e07ee-115">Zmiana wartości tych pól publicznych nie powoduje zmiany zachowania typów .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e07ee-115">Changing the values of these public fields does not alter the behavior of .NET Framework types.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e07ee-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e07ee-116">See also</span></span>

- [<span data-ttu-id="e07ee-117">Wytyczne dotyczące bezpiecznego programowania</span><span class="sxs-lookup"><span data-stu-id="e07ee-117">Secure Coding Guidelines</span></span>](../../standard/security/secure-coding-guidelines.md)

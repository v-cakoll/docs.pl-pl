---
title: Bezpieczeństwo i publiczne pola tablicy tylko do odczytu
ms.date: 03/30/2017
helpviewer_keywords:
- security [.NET Framework], public read-only array fields
ms.assetid: 3df28dee-2a9f-40ff-9852-bfdbe59c27f3
ms.openlocfilehash: 2df4acc0606e4fe8fccee4a8acc6ab744dcbbb71
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452711"
---
# <a name="security-and-public-read-only-array-fields"></a><span data-ttu-id="c4a53-102">Bezpieczeństwo i publiczne pola tablicy tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="c4a53-102">Security and Public Read-only Array Fields</span></span>
<span data-ttu-id="c4a53-103">Nie używaj pól tablicy publicznej tylko do odczytu z bibliotek zarządzanych, aby zdefiniować zachowanie granic lub zabezpieczenia aplikacji, ponieważ można modyfikować pola tablicy publicznej tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="c4a53-103">Never use read-only public array fields from managed libraries to define the boundary behavior or security of your applications because read-only public array fields can be modified.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c4a53-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c4a53-104">Remarks</span></span>  

<span data-ttu-id="c4a53-105">Niektóre klasy .NET zawierają pola publiczne tylko do odczytu, które zawierają parametry graniczne specyficzne dla platformy.</span><span class="sxs-lookup"><span data-stu-id="c4a53-105">Some .NET classes include read-only public fields that contain platform-specific boundary parameters.</span></span> <span data-ttu-id="c4a53-106">Na przykład pole <xref:System.IO.Path.InvalidPathChars> jest tablicą opisującą znaki, które nie są dozwolone w ciągu ścieżki do pliku.</span><span class="sxs-lookup"><span data-stu-id="c4a53-106">For example, the <xref:System.IO.Path.InvalidPathChars> field is an array that describes the characters that are not allowed in a file path string.</span></span> <span data-ttu-id="c4a53-107">W środowisku .NET są obecne wiele podobnych pól.</span><span class="sxs-lookup"><span data-stu-id="c4a53-107">Many similar fields are present throughout .NET.</span></span>  
  
 <span data-ttu-id="c4a53-108">Wartości publicznych pól tylko do odczytu, takich jak <xref:System.IO.Path.InvalidPathChars>, mogą być modyfikowane przez kod lub kod, który współużytkuje domenę aplikacji Twojego kodu.</span><span class="sxs-lookup"><span data-stu-id="c4a53-108">The values of public read-only fields like <xref:System.IO.Path.InvalidPathChars> can be modified by your code or code that shares your code’s application domain.</span></span>  <span data-ttu-id="c4a53-109">Nie należy używać pól tablic publicznych tylko do odczytu, takich jak to, aby zdefiniować zachowanie granic aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c4a53-109">You should not use read-only public array fields like this to define the boundary behavior of your applications.</span></span>  <span data-ttu-id="c4a53-110">Jeśli to zrobisz, złośliwy kod może zmienić definicje granic i użyć kodu w nieoczekiwany sposób.</span><span class="sxs-lookup"><span data-stu-id="c4a53-110">If you do, malicious code can alter the boundary definitions and use your code in unexpected ways.</span></span>  
  
 <span data-ttu-id="c4a53-111">W wersji 2,0 i nowszych .NET Framework należy używać metod, które zwracają nową tablicę zamiast używać publicznych pól tablic.</span><span class="sxs-lookup"><span data-stu-id="c4a53-111">In version 2.0 and later of the .NET Framework, you should use methods that return a new array instead of using public array fields.</span></span>  <span data-ttu-id="c4a53-112">Na przykład zamiast używać pola <xref:System.IO.Path.InvalidPathChars>, należy użyć metody <xref:System.IO.Path.GetInvalidPathChars%2A>.</span><span class="sxs-lookup"><span data-stu-id="c4a53-112">For example, instead of using the <xref:System.IO.Path.InvalidPathChars> field, you should use the <xref:System.IO.Path.GetInvalidPathChars%2A> method.</span></span>  
  
 <span data-ttu-id="c4a53-113">Należy zauważyć, że typy .NET Framework nie używają publicznych pól do wewnętrznego definiowania typów granic.</span><span class="sxs-lookup"><span data-stu-id="c4a53-113">Note that the .NET Framework types do not use the public fields to define boundary types internally.</span></span>  <span data-ttu-id="c4a53-114">Zamiast tego .NET Framework używa oddzielnych pól prywatnych.</span><span class="sxs-lookup"><span data-stu-id="c4a53-114">Instead, the .NET Framework uses separate private fields.</span></span>  <span data-ttu-id="c4a53-115">Zmiana wartości tych pól publicznych nie powoduje zmiany zachowania typów .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c4a53-115">Changing the values of these public fields does not alter the behavior of .NET Framework types.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4a53-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c4a53-116">See also</span></span>

- [<span data-ttu-id="c4a53-117">Wytyczne dotyczące bezpiecznego programowania</span><span class="sxs-lookup"><span data-stu-id="c4a53-117">Secure Coding Guidelines</span></span>](../../standard/security/secure-coding-guidelines.md)

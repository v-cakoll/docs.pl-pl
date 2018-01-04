---
title: "Bezpieczeństwo i publiczne pola tablicy tylko do odczytu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: security [.NET Framework], public read-only array fields
ms.assetid: 3df28dee-2a9f-40ff-9852-bfdbe59c27f3
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d86d054d3a5a4e10b8efcc3292f3a18ea37f9b87
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="security-and-public-read-only-array-fields"></a><span data-ttu-id="29f5b-102">Bezpieczeństwo i publiczne pola tablicy tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="29f5b-102">Security and Public Read-only Array Fields</span></span>
<span data-ttu-id="29f5b-103">Nigdy nie używaj tylko do odczytu publiczne pola tablicy z bibliotek zarządzanych do definiowania zachowania granic lub zabezpieczeń aplikacji, ponieważ mogą być modyfikowane tylko do odczytu publiczne pola tablicy.</span><span class="sxs-lookup"><span data-stu-id="29f5b-103">Never use read-only public array fields from managed libraries to define the boundary behavior or security of your applications because read-only public array fields can be modified.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="29f5b-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="29f5b-104">Remarks</span></span>  
 <span data-ttu-id="29f5b-105">Niektóre klasy framework .NET zawierają tylko do odczytu pola publiczne, zawierających parametry specyficzne dla platformy granic.</span><span class="sxs-lookup"><span data-stu-id="29f5b-105">Some .NET framework classes include read-only public fields that contain platform-specific boundary parameters.</span></span>  <span data-ttu-id="29f5b-106">Na przykład <xref:System.IO.Path.InvalidPathChars> pole jest tablicę, która opisuje znaki, które nie są dozwolone w ciągu ścieżki pliku.</span><span class="sxs-lookup"><span data-stu-id="29f5b-106">For example, the <xref:System.IO.Path.InvalidPathChars> field is an array that describes the characters that are not allowed in a file path string.</span></span>  <span data-ttu-id="29f5b-107">Wiele podobnych pól znajdują się w programie .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="29f5b-107">Many similar fields are present throughout the .NET Framework.</span></span>  
  
 <span data-ttu-id="29f5b-108">Wartości pola publiczne tylko do odczytu, takich jak <xref:System.IO.Path.InvalidPathChars> można zmodyfikować przez kod lub kod, który udostępnia swój kod domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="29f5b-108">The values of public read-only fields like <xref:System.IO.Path.InvalidPathChars> can be modified by your code or code that shares your code’s application domain.</span></span>  <span data-ttu-id="29f5b-109">Nie należy używać tylko do odczytu publiczne pola tablicy takie Definiowanie zachowania granic aplikacji.</span><span class="sxs-lookup"><span data-stu-id="29f5b-109">You should not use read-only public array fields like this to define the boundary behavior of your applications.</span></span>  <span data-ttu-id="29f5b-110">Jeśli to zrobisz, złośliwy kod może zmiany definicji granic i używać kodu w nieoczekiwany sposób.</span><span class="sxs-lookup"><span data-stu-id="29f5b-110">If you do, malicious code can alter the boundary definitions and use your code in unexpected ways.</span></span>  
  
 <span data-ttu-id="29f5b-111">W wersji 2.0 lub nowszej programu .NET Framework należy użyć metody, które zwracają nowe tablicy zamiast publiczne pola tablicy.</span><span class="sxs-lookup"><span data-stu-id="29f5b-111">In version 2.0 and later of the .NET Framework, you should use methods that return a new array instead of using public array fields.</span></span>  <span data-ttu-id="29f5b-112">Na przykład zamiast <xref:System.IO.Path.InvalidPathChars> pola, należy użyć <xref:System.IO.Path.GetInvalidPathChars%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="29f5b-112">For example, instead of using the <xref:System.IO.Path.InvalidPathChars> field, you should use the <xref:System.IO.Path.GetInvalidPathChars%2A> method.</span></span>  
  
 <span data-ttu-id="29f5b-113">Należy pamiętać, że typy .NET Framework nie pola publiczne wewnętrznie określenie typów granic.</span><span class="sxs-lookup"><span data-stu-id="29f5b-113">Note that the .NET Framework types do not use the public fields to define boundary types internally.</span></span>  <span data-ttu-id="29f5b-114">Zamiast tego programu .NET Framework używa oddzielnych pól prywatnych.</span><span class="sxs-lookup"><span data-stu-id="29f5b-114">Instead, the .NET Framework uses separate private fields.</span></span>  <span data-ttu-id="29f5b-115">Zmiana wartości te pola publiczne nie zmienia zachowanie typów .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="29f5b-115">Changing the values of these public fields does not alter the behavior of .NET Framework types.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29f5b-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="29f5b-116">See Also</span></span>  
 [<span data-ttu-id="29f5b-117">Wytyczne dotyczące bezpiecznego programowania</span><span class="sxs-lookup"><span data-stu-id="29f5b-117">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)

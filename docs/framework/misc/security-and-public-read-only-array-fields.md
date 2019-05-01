---
title: Bezpieczeństwo i publiczne pola tablicy tylko do odczytu
ms.date: 03/30/2017
helpviewer_keywords:
- security [.NET Framework], public read-only array fields
ms.assetid: 3df28dee-2a9f-40ff-9852-bfdbe59c27f3
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 19b5ad73150697c1442056642a1b11d504ecc426
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61869749"
---
# <a name="security-and-public-read-only-array-fields"></a><span data-ttu-id="907e0-102">Bezpieczeństwo i publiczne pola tablicy tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="907e0-102">Security and Public Read-only Array Fields</span></span>
<span data-ttu-id="907e0-103">Nigdy nie używaj tylko do odczytu publiczne pola tablicy z zarządzanych bibliotek do definiowania zachowania granic lub bezpieczeństwem Twoich aplikacji, ponieważ tylko do odczytu publiczne pola tablicy można modyfikować.</span><span class="sxs-lookup"><span data-stu-id="907e0-103">Never use read-only public array fields from managed libraries to define the boundary behavior or security of your applications because read-only public array fields can be modified.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="907e0-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="907e0-104">Remarks</span></span>  
 <span data-ttu-id="907e0-105">Niektóre klasy framework .NET zawierają tylko do odczytu publicznych pola, które zawierają parametry specyficzne dla platformy granic.</span><span class="sxs-lookup"><span data-stu-id="907e0-105">Some .NET framework classes include read-only public fields that contain platform-specific boundary parameters.</span></span>  <span data-ttu-id="907e0-106">Na przykład <xref:System.IO.Path.InvalidPathChars> pole jest tablica, która opisuje znaki, które nie są dozwolone w ciąg ścieżki pliku.</span><span class="sxs-lookup"><span data-stu-id="907e0-106">For example, the <xref:System.IO.Path.InvalidPathChars> field is an array that describes the characters that are not allowed in a file path string.</span></span>  <span data-ttu-id="907e0-107">Wiele podobnych pól znajdują się w całym programie .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="907e0-107">Many similar fields are present throughout the .NET Framework.</span></span>  
  
 <span data-ttu-id="907e0-108">Wartości pola publiczne tylko do odczytu, takich jak <xref:System.IO.Path.InvalidPathChars> można zmodyfikować przez kod lub kod, który udostępnia swój kod domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="907e0-108">The values of public read-only fields like <xref:System.IO.Path.InvalidPathChars> can be modified by your code or code that shares your code’s application domain.</span></span>  <span data-ttu-id="907e0-109">Nie należy używać tylko do odczytu publiczne pola tablicy następująco do określania zachowania granic aplikacji.</span><span class="sxs-lookup"><span data-stu-id="907e0-109">You should not use read-only public array fields like this to define the boundary behavior of your applications.</span></span>  <span data-ttu-id="907e0-110">Jeśli to zrobisz, złośliwy kod może zmiany definicji granic i użyciu kodu w nieoczekiwany sposób.</span><span class="sxs-lookup"><span data-stu-id="907e0-110">If you do, malicious code can alter the boundary definitions and use your code in unexpected ways.</span></span>  
  
 <span data-ttu-id="907e0-111">W wersji 2.0 i nowszej programu .NET Framework należy użyć metody, które zwracają nową tablicę zamiast publiczne pola tablicy.</span><span class="sxs-lookup"><span data-stu-id="907e0-111">In version 2.0 and later of the .NET Framework, you should use methods that return a new array instead of using public array fields.</span></span>  <span data-ttu-id="907e0-112">Na przykład, zamiast <xref:System.IO.Path.InvalidPathChars> pola, należy użyć <xref:System.IO.Path.GetInvalidPathChars%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="907e0-112">For example, instead of using the <xref:System.IO.Path.InvalidPathChars> field, you should use the <xref:System.IO.Path.GetInvalidPathChars%2A> method.</span></span>  
  
 <span data-ttu-id="907e0-113">Należy pamiętać, że typów programu .NET Framework nie należy używać pola publiczne do definiowania typów granic wewnętrznie.</span><span class="sxs-lookup"><span data-stu-id="907e0-113">Note that the .NET Framework types do not use the public fields to define boundary types internally.</span></span>  <span data-ttu-id="907e0-114">Zamiast programu .NET Framework używa oddzielnych pól prywatnych.</span><span class="sxs-lookup"><span data-stu-id="907e0-114">Instead, the .NET Framework uses separate private fields.</span></span>  <span data-ttu-id="907e0-115">Zmiana wartości te pola publiczne nie zmienia zachowanie typów programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="907e0-115">Changing the values of these public fields does not alter the behavior of .NET Framework types.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="907e0-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="907e0-116">See also</span></span>

- [<span data-ttu-id="907e0-117">Wytyczne dotyczące bezpiecznego programowania</span><span class="sxs-lookup"><span data-stu-id="907e0-117">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)

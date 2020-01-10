---
title: Zabezpieczenia i generowanie kodu na bieżąco
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- code security, on-the-fly code generation
- on-the-fly code generation
- security [.NET Framework], on-the-fly code generation
- secure coding, on-the-fly code generation
ms.assetid: 6d221724-bb21-4d76-90c3-0ee2a2e69be2
ms.openlocfilehash: 64ddcc6a379e5719eb734eede13e576a707696fe
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705889"
---
# <a name="security-and-on-the-fly-code-generation"></a><span data-ttu-id="d3667-102">Zabezpieczenia i generowanie kodu na bieżąco</span><span class="sxs-lookup"><span data-stu-id="d3667-102">Security and On-the-Fly Code Generation</span></span>
<span data-ttu-id="d3667-103">Niektóre biblioteki działają przez generowanie kodu i uruchamianie go w celu wykonania niektórych operacji dla obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="d3667-103">Some libraries operate by generating code and running it to perform some operation for the caller.</span></span> <span data-ttu-id="d3667-104">Podstawowy problem polega na wygenerowaniu kodu w imieniu kodu o niższym zaufaniu i uruchomieniu go na wyższym poziomie zaufania.</span><span class="sxs-lookup"><span data-stu-id="d3667-104">The basic problem is generating code on behalf of lesser-trust code and running it at a higher trust.</span></span> <span data-ttu-id="d3667-105">Problem pogorszy się, gdy obiekt wywołujący może wpływać na generowanie kodu, dlatego należy się upewnić, że generowany jest tylko kod, który jest uważany za bezpieczny.</span><span class="sxs-lookup"><span data-stu-id="d3667-105">The problem worsens when the caller can influence code generation, so you must ensure that only code you consider safe is generated.</span></span>  
  
 <span data-ttu-id="d3667-106">Musisz dokładnie poznać kod, który jest generowany przez cały czas.</span><span class="sxs-lookup"><span data-stu-id="d3667-106">You need to know exactly what code you are generating at all times.</span></span> <span data-ttu-id="d3667-107">Oznacza to, że musisz mieć ścisłe kontrolki dla wszystkich wartości, które otrzymujesz od użytkownika, czy są to ciągi ujęte w cudzysłów (które powinny zostać zmienione, aby nie zawierały nieoczekiwanych elementów kodu), identyfikatory (które należy sprawdzić, aby sprawdzić, czy są one prawidłowe identyfikatory) lub inne.</span><span class="sxs-lookup"><span data-stu-id="d3667-107">This means that you must have strict controls on any values that you get from a user, be they quote-enclosed strings (which should be escaped so they cannot include unexpected code elements), identifiers (which should be checked to verify that they are valid identifiers), or anything else.</span></span> <span data-ttu-id="d3667-108">Identyfikatory mogą być niebezpieczne, ponieważ skompilowany zestaw można zmodyfikować tak, aby jego identyfikatory zawierały nietypowe znaki, które prawdopodobnie spowodują jego przerwanie (chociaż jest to rzadko występująca Luka w zabezpieczeniach).</span><span class="sxs-lookup"><span data-stu-id="d3667-108">Identifiers can be dangerous because a compiled assembly can be modified so that its identifiers contain strange characters, which will probably break it (although this is rarely a security vulnerability).</span></span>  
  
 <span data-ttu-id="d3667-109">Zaleca się generowanie kodu przy użyciu emisji odbicia, co często pomaga uniknąć wielu z tych problemów.</span><span class="sxs-lookup"><span data-stu-id="d3667-109">It is recommended that you generate code with reflection emit, which often helps you avoid many of these problems.</span></span>  
  
 <span data-ttu-id="d3667-110">Podczas kompilowania kodu należy rozważyć, czy istnieje pewien sposób, w jaki złośliwy program mógłby go zmodyfikować.</span><span class="sxs-lookup"><span data-stu-id="d3667-110">When you compile the code, consider whether there is some way a malicious program could modify it.</span></span> <span data-ttu-id="d3667-111">Czy istnieje niewielkie okno czasu, w którym złośliwy kod może zmienić kod źródłowy na dysku, zanim kompilator go odczyta lub zanim kod załaduje plik dll?</span><span class="sxs-lookup"><span data-stu-id="d3667-111">Is there a small window of time during which malicious code can change source code on disk before the compiler reads it or before your code loads the .dll file?</span></span> <span data-ttu-id="d3667-112">W takim przypadku należy chronić katalog zawierający te pliki przy użyciu listy Access Control w systemie plików, zgodnie z potrzebami.</span><span class="sxs-lookup"><span data-stu-id="d3667-112">If so, you must protect the directory containing these files, using an Access Control List in the file system, as appropriate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3667-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d3667-113">See also</span></span>

- [<span data-ttu-id="d3667-114">Wytyczne dotyczące bezpiecznego programowania</span><span class="sxs-lookup"><span data-stu-id="d3667-114">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)

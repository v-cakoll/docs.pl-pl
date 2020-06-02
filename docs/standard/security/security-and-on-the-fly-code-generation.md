---
title: Zabezpieczenia i generowanie kodu na bieżąco
description: Generowanie kodu w imieniu niemniejszego zaufania kodu, który jest uruchamiany na wyższym poziomie zaufania, stanowi zagrożenie bezpieczeństwa, zwłaszcza gdy obiekt wywołujący może wpływać na generowanie kodu.
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- code security, on-the-fly code generation
- on-the-fly code generation
- security [.NET Framework], on-the-fly code generation
- secure coding, on-the-fly code generation
ms.assetid: 6d221724-bb21-4d76-90c3-0ee2a2e69be2
ms.openlocfilehash: 7e5168aa9305c559cf5ea2fb197b2c23ce2a05b0
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291035"
---
# <a name="security-and-on-the-fly-code-generation"></a><span data-ttu-id="7cd04-103">Zabezpieczenia i generowanie kodu na bieżąco</span><span class="sxs-lookup"><span data-stu-id="7cd04-103">Security and On-the-Fly Code Generation</span></span>
<span data-ttu-id="7cd04-104">Niektóre biblioteki działają przez generowanie kodu i uruchamianie go w celu wykonania niektórych operacji dla obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="7cd04-104">Some libraries operate by generating code and running it to perform some operation for the caller.</span></span> <span data-ttu-id="7cd04-105">Podstawowy problem polega na wygenerowaniu kodu w imieniu kodu o niższym zaufaniu i uruchomieniu go na wyższym poziomie zaufania.</span><span class="sxs-lookup"><span data-stu-id="7cd04-105">The basic problem is generating code on behalf of lesser-trust code and running it at a higher trust.</span></span> <span data-ttu-id="7cd04-106">Problem pogorszy się, gdy obiekt wywołujący może wpływać na generowanie kodu, dlatego należy się upewnić, że generowany jest tylko kod, który jest uważany za bezpieczny.</span><span class="sxs-lookup"><span data-stu-id="7cd04-106">The problem worsens when the caller can influence code generation, so you must ensure that only code you consider safe is generated.</span></span>  
  
 <span data-ttu-id="7cd04-107">Musisz dokładnie poznać kod, który jest generowany przez cały czas.</span><span class="sxs-lookup"><span data-stu-id="7cd04-107">You need to know exactly what code you are generating at all times.</span></span> <span data-ttu-id="7cd04-108">Oznacza to, że musisz mieć ścisłe kontrolki dla wszystkich wartości, które otrzymujesz od użytkownika, czy są to ciągi ujęte w cudzysłów (które należy zmienić, aby nie mogli zawierać nieoczekiwanych elementów kodu), identyfikatory (które powinny być sprawdzane w celu sprawdzenia, czy są prawidłowymi identyfikatorami) lub inne.</span><span class="sxs-lookup"><span data-stu-id="7cd04-108">This means that you must have strict controls on any values that you get from a user, be they quote-enclosed strings (which should be escaped so they cannot include unexpected code elements), identifiers (which should be checked to verify that they are valid identifiers), or anything else.</span></span> <span data-ttu-id="7cd04-109">Identyfikatory mogą być niebezpieczne, ponieważ skompilowany zestaw można zmodyfikować tak, aby jego identyfikatory zawierały nietypowe znaki, które prawdopodobnie spowodują jego przerwanie (chociaż jest to rzadko występująca Luka w zabezpieczeniach).</span><span class="sxs-lookup"><span data-stu-id="7cd04-109">Identifiers can be dangerous because a compiled assembly can be modified so that its identifiers contain strange characters, which will probably break it (although this is rarely a security vulnerability).</span></span>  
  
 <span data-ttu-id="7cd04-110">Zaleca się generowanie kodu przy użyciu emisji odbicia, co często pomaga uniknąć wielu z tych problemów.</span><span class="sxs-lookup"><span data-stu-id="7cd04-110">It is recommended that you generate code with reflection emit, which often helps you avoid many of these problems.</span></span>  
  
 <span data-ttu-id="7cd04-111">Podczas kompilowania kodu należy rozważyć, czy istnieje pewien sposób, w jaki złośliwy program mógłby go zmodyfikować.</span><span class="sxs-lookup"><span data-stu-id="7cd04-111">When you compile the code, consider whether there is some way a malicious program could modify it.</span></span> <span data-ttu-id="7cd04-112">Czy istnieje niewielkie okno czasu, w którym złośliwy kod może zmienić kod źródłowy na dysku, zanim kompilator go odczyta lub zanim kod załaduje plik dll?</span><span class="sxs-lookup"><span data-stu-id="7cd04-112">Is there a small window of time during which malicious code can change source code on disk before the compiler reads it or before your code loads the .dll file?</span></span> <span data-ttu-id="7cd04-113">W takim przypadku należy chronić katalog zawierający te pliki przy użyciu listy Access Control w systemie plików, zgodnie z potrzebami.</span><span class="sxs-lookup"><span data-stu-id="7cd04-113">If so, you must protect the directory containing these files, using an Access Control List in the file system, as appropriate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7cd04-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7cd04-114">See also</span></span>

- [<span data-ttu-id="7cd04-115">Wytyczne dotyczące bezpiecznego programowania</span><span class="sxs-lookup"><span data-stu-id="7cd04-115">Secure Coding Guidelines</span></span>](secure-coding-guidelines.md)

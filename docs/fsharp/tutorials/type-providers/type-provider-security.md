---
title: Zabezpieczenia dostawcy typów
description: 'Więcej informacji o zabezpieczenia dostawcy typów w języku F #, łącznie ze sposobem zmiany ustawień zaufania dla dostawcy typów.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 4f0b55062aec6c560112fe10ca4df77f42493011
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="type-provider-security"></a><span data-ttu-id="c6d90-103">Zabezpieczenia dostawcy typów</span><span class="sxs-lookup"><span data-stu-id="c6d90-103">Type Provider Security</span></span>

<span data-ttu-id="c6d90-104">Dostawcy typów to zestawy (dll) odwołuje się programu F # projekt lub skrypt zawierające kod, aby nawiązać połączenia z zewnętrznymi źródłami danych, a następnie publikować informacje o tym typie środowiska typu F #.</span><span class="sxs-lookup"><span data-stu-id="c6d90-104">Type providers are assemblies (DLLs) referenced by your F# project or script that contain code to connect to external data sources and surface this type information to the F# type environment.</span></span> <span data-ttu-id="c6d90-105">Zazwyczaj kodu w przywoływanych zestawach jest uruchamiany tylko kompilacji, a następnie wykonania kodu (lub w przypadku skryptu, wyślij kod do narzędzia F # Interactive).</span><span class="sxs-lookup"><span data-stu-id="c6d90-105">Typically, code in referenced assemblies is only run when you compile and then execute the code (or in the case of a script, send the code to F# Interactive).</span></span> <span data-ttu-id="c6d90-106">Jednak zestawu dostawcy typu zostanie uruchomiony w programie Visual Studio podczas kod jest jedynie w edytorze.</span><span class="sxs-lookup"><span data-stu-id="c6d90-106">However, a type provider assembly will run inside Visual Studio when the code is merely browsed in the editor.</span></span> <span data-ttu-id="c6d90-107">Dzieje się tak, ponieważ typ dostawcy muszą Uruchom, aby dodać dodatkowe informacje do edytora, takiego jak szybka podpowiedź, zakończeń IntelliSense i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="c6d90-107">This happens because type providers need to run to add extra information to the editor, such as Quick Info tooltips, IntelliSense completions, and so on.</span></span> <span data-ttu-id="c6d90-108">W związku z tym istnieją zagadnienia dotyczące dodatkowych zabezpieczeń dla typu zestawy dostawcy, ponieważ są automatycznie uruchamiane wewnątrz procesu programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c6d90-108">As a result, there are extra security considerations for type provider assemblies, since they run automatically inside the Visual Studio process.</span></span>


## <a name="security-warning-dialog"></a><span data-ttu-id="c6d90-109">Okno dialogowe ostrzeżenia o zabezpieczeniach</span><span class="sxs-lookup"><span data-stu-id="c6d90-109">Security Warning Dialog</span></span>
<span data-ttu-id="c6d90-110">Korzystając z zestawu dostawcy określonego typu po raz pierwszy, program Visual Studio Wyświetla okno dialogowe zabezpieczeń, które ostrzega o tym, że dostawca typów jest uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="c6d90-110">When using a particular type provider assembly for the first time, Visual Studio displays a security dialog that warns you that the type provider is about to run.</span></span> <span data-ttu-id="c6d90-111">Przed Visual Studio ładuje typ dostawcy, daje możliwość zdecydować, jeśli ufasz temu określonego dostawcy.</span><span class="sxs-lookup"><span data-stu-id="c6d90-111">Before Visual Studio loads the type provider, it gives you the opportunity to decide if you trust this particular provider.</span></span> <span data-ttu-id="c6d90-112">Jeśli ufasz źródłu typu dostawcy, następnie wybierz pozycję "I zaufanie ten dostawca typów".</span><span class="sxs-lookup"><span data-stu-id="c6d90-112">If you trust the source of the type provider, then select "I trust this type provider."</span></span> <span data-ttu-id="c6d90-113">Jeśli nie ufasz źródło typ dostawcy, następnie wybierz pozycję "I nie masz zaufania tego typu dostawcy."</span><span class="sxs-lookup"><span data-stu-id="c6d90-113">If you do not trust the source of the type provider, then select "I do not trust this type provider."</span></span> <span data-ttu-id="c6d90-114">Zaufanie dostawcy umożliwia uruchamianie w programie Visual Studio i podaj IntelliSense i tworzenia funkcji.</span><span class="sxs-lookup"><span data-stu-id="c6d90-114">Trusting the provider enables it to run inside Visual Studio and provide IntelliSense and build features.</span></span> <span data-ttu-id="c6d90-115">Jednak w przypadku złośliwego typ dostawcy samego uruchomienia jej kodu może naruszyć bezpieczeństwo komputera.</span><span class="sxs-lookup"><span data-stu-id="c6d90-115">But if the type provider itself is malicious, running its code could compromise your machine.</span></span>

<span data-ttu-id="c6d90-116">Jeśli projekt zawiera kod, który odwołuje się do dostawców typów, które wybrano w oknie dialogowym niezaufane, następnie w czasie kompilacji, kompilator będzie zgłaszać błąd, który wskazuje, że dostawca typów jest niezaufanych.</span><span class="sxs-lookup"><span data-stu-id="c6d90-116">If your project contains code that references type providers that you chose in the dialog not to trust, then at compile time, the compiler will report an error that indicates that the type provider is untrusted.</span></span> <span data-ttu-id="c6d90-117">Żadnych typów, które są zależne od dostawcy typów niezaufanych są oznaczone czerwoną zygzaki.</span><span class="sxs-lookup"><span data-stu-id="c6d90-117">Any types that are dependent on the untrusted type provider are indicated by red squiggles.</span></span> <span data-ttu-id="c6d90-118">Jest to bezpieczne przeglądanie kodu w edytorze.</span><span class="sxs-lookup"><span data-stu-id="c6d90-118">It is safe to browse the code in the editor.</span></span>

<span data-ttu-id="c6d90-119">Jeśli zdecydujesz się zmienić ustawienie zaufania bezpośrednio w programie Visual Studio, wykonaj następujące kroki.</span><span class="sxs-lookup"><span data-stu-id="c6d90-119">If you decide to change the trust setting directly in Visual Studio, perform the following steps.</span></span>


#### <a name="to-change-the-trust-settings-for-type-providers"></a><span data-ttu-id="c6d90-120">Aby zmienić ustawienia zaufania dostawców typów</span><span class="sxs-lookup"><span data-stu-id="c6d90-120">To change the trust settings for type providers</span></span>

1. <span data-ttu-id="c6d90-121">Na `Tools` menu, wybierz opcję `Options`i rozwiń `F# Tools` węzła.</span><span class="sxs-lookup"><span data-stu-id="c6d90-121">On the `Tools` menu, select `Options`, and expand the `F# Tools` node.</span></span>
<br />

2. <span data-ttu-id="c6d90-122">Wybierz `Type Providers`, na liście dostawców typów, zaznacz pole wyboru dla zaufanych dostawców typów i usuń zaznaczenie pola wyboru dla tych nie ufasz.</span><span class="sxs-lookup"><span data-stu-id="c6d90-122">Select `Type Providers`, and in the list of type providers, select the check box for type providers you trust, and clear the check box for those you don't trust.</span></span>
<br />


## <a name="see-also"></a><span data-ttu-id="c6d90-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c6d90-123">See Also</span></span>
[<span data-ttu-id="c6d90-124">Dostawcy typów</span><span class="sxs-lookup"><span data-stu-id="c6d90-124">Type Providers</span></span>](index.md)

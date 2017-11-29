---
title: "Zabezpieczenia dostawcy typów"
description: "Więcej informacji o zabezpieczenia dostawcy typów w języku F #, łącznie ze sposobem zmiany ustawień zaufania dla dostawcy typów."
keywords: "Visual f #, f #, funkcjonalności programowania"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 9c5a8a1f-5a31-490d-83c0-8beabda75c78
ms.openlocfilehash: c8f03ee90d4dce1d3484a9dfe8951d500d509a2b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="type-provider-security"></a><span data-ttu-id="b9ada-104">Zabezpieczenia dostawcy typów</span><span class="sxs-lookup"><span data-stu-id="b9ada-104">Type Provider Security</span></span>

<span data-ttu-id="b9ada-105">Dostawcy typów to zestawy (dll) odwołuje się programu F # projekt lub skrypt zawierające kod, aby nawiązać połączenia z zewnętrznymi źródłami danych, a następnie publikować informacje o tym typie środowiska typu F #.</span><span class="sxs-lookup"><span data-stu-id="b9ada-105">Type providers are assemblies (DLLs) referenced by your F# project or script that contain code to connect to external data sources and surface this type information to the F# type environment.</span></span> <span data-ttu-id="b9ada-106">Zazwyczaj kodu w przywoływanych zestawach jest uruchamiany tylko kompilacji, a następnie wykonania kodu (lub w przypadku skryptu, wyślij kod do narzędzia F # Interactive).</span><span class="sxs-lookup"><span data-stu-id="b9ada-106">Typically, code in referenced assemblies is only run when you compile and then execute the code (or in the case of a script, send the code to F# Interactive).</span></span> <span data-ttu-id="b9ada-107">Jednak zestawu dostawcy typu zostanie uruchomiony w programie Visual Studio podczas kod jest jedynie w edytorze.</span><span class="sxs-lookup"><span data-stu-id="b9ada-107">However, a type provider assembly will run inside Visual Studio when the code is merely browsed in the editor.</span></span> <span data-ttu-id="b9ada-108">Dzieje się tak, ponieważ typ dostawcy muszą Uruchom, aby dodać dodatkowe informacje do edytora, takiego jak szybka podpowiedź, zakończeń IntelliSense i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="b9ada-108">This happens because type providers need to run to add extra information to the editor, such as Quick Info tooltips, IntelliSense completions, and so on.</span></span> <span data-ttu-id="b9ada-109">W związku z tym istnieją zagadnienia dotyczące dodatkowych zabezpieczeń dla typu zestawy dostawcy, ponieważ są automatycznie uruchamiane wewnątrz procesu programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b9ada-109">As a result, there are extra security considerations for type provider assemblies, since they run automatically inside the Visual Studio process.</span></span>


## <a name="security-warning-dialog"></a><span data-ttu-id="b9ada-110">Okno dialogowe ostrzeżenia o zabezpieczeniach</span><span class="sxs-lookup"><span data-stu-id="b9ada-110">Security Warning Dialog</span></span>
<span data-ttu-id="b9ada-111">Korzystając z zestawu dostawcy określonego typu po raz pierwszy, program Visual Studio Wyświetla okno dialogowe zabezpieczeń, które ostrzega o tym, że dostawca typów jest uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="b9ada-111">When using a particular type provider assembly for the first time, Visual Studio displays a security dialog that warns you that the type provider is about to run.</span></span> <span data-ttu-id="b9ada-112">Przed Visual Studio ładuje typ dostawcy, daje możliwość zdecydować, jeśli ufasz temu określonego dostawcy.</span><span class="sxs-lookup"><span data-stu-id="b9ada-112">Before Visual Studio loads the type provider, it gives you the opportunity to decide if you trust this particular provider.</span></span> <span data-ttu-id="b9ada-113">Jeśli ufasz źródłu typu dostawcy, następnie wybierz pozycję "I zaufanie ten dostawca typów".</span><span class="sxs-lookup"><span data-stu-id="b9ada-113">If you trust the source of the type provider, then select "I trust this type provider."</span></span> <span data-ttu-id="b9ada-114">Jeśli nie ufasz źródło typ dostawcy, następnie wybierz pozycję "I nie masz zaufania tego typu dostawcy."</span><span class="sxs-lookup"><span data-stu-id="b9ada-114">If you do not trust the source of the type provider, then select "I do not trust this type provider."</span></span> <span data-ttu-id="b9ada-115">Zaufanie dostawcy umożliwia uruchamianie w programie Visual Studio i podaj IntelliSense i tworzenia funkcji.</span><span class="sxs-lookup"><span data-stu-id="b9ada-115">Trusting the provider enables it to run inside Visual Studio and provide IntelliSense and build features.</span></span> <span data-ttu-id="b9ada-116">Jednak w przypadku złośliwego typ dostawcy samego uruchomienia jej kodu może naruszyć bezpieczeństwo komputera.</span><span class="sxs-lookup"><span data-stu-id="b9ada-116">But if the type provider itself is malicious, running its code could compromise your machine.</span></span>

<span data-ttu-id="b9ada-117">Jeśli projekt zawiera kod, który odwołuje się do dostawców typów, które wybrano w oknie dialogowym niezaufane, następnie w czasie kompilacji, kompilator będzie zgłaszać błąd, który wskazuje, że dostawca typów jest niezaufanych.</span><span class="sxs-lookup"><span data-stu-id="b9ada-117">If your project contains code that references type providers that you chose in the dialog not to trust, then at compile time, the compiler will report an error that indicates that the type provider is untrusted.</span></span> <span data-ttu-id="b9ada-118">Żadnych typów, które są zależne od dostawcy typów niezaufanych są oznaczone czerwoną zygzaki.</span><span class="sxs-lookup"><span data-stu-id="b9ada-118">Any types that are dependent on the untrusted type provider are indicated by red squiggles.</span></span> <span data-ttu-id="b9ada-119">Jest to bezpieczne przeglądanie kodu w edytorze.</span><span class="sxs-lookup"><span data-stu-id="b9ada-119">It is safe to browse the code in the editor.</span></span>

<span data-ttu-id="b9ada-120">Jeśli zdecydujesz się zmienić ustawienie zaufania bezpośrednio w programie Visual Studio, wykonaj następujące kroki.</span><span class="sxs-lookup"><span data-stu-id="b9ada-120">If you decide to change the trust setting directly in Visual Studio, perform the following steps.</span></span>


#### <a name="to-change-the-trust-settings-for-type-providers"></a><span data-ttu-id="b9ada-121">Aby zmienić ustawienia zaufania dostawców typów</span><span class="sxs-lookup"><span data-stu-id="b9ada-121">To change the trust settings for type providers</span></span>

1. <span data-ttu-id="b9ada-122">Na `Tools` menu, wybierz opcję `Options`i rozwiń `F# Tools` węzła.</span><span class="sxs-lookup"><span data-stu-id="b9ada-122">On the `Tools` menu, select `Options`, and expand the `F# Tools` node.</span></span>
<br />

2. <span data-ttu-id="b9ada-123">Wybierz `Type Providers`, na liście dostawców typów, zaznacz pole wyboru dla zaufanych dostawców typów i usuń zaznaczenie pola wyboru dla tych nie ufasz.</span><span class="sxs-lookup"><span data-stu-id="b9ada-123">Select `Type Providers`, and in the list of type providers, select the check box for type providers you trust, and clear the check box for those you don't trust.</span></span>
<br />


## <a name="see-also"></a><span data-ttu-id="b9ada-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b9ada-124">See Also</span></span>
[<span data-ttu-id="b9ada-125">Dostawcy typów</span><span class="sxs-lookup"><span data-stu-id="b9ada-125">Type Providers</span></span>](index.md)

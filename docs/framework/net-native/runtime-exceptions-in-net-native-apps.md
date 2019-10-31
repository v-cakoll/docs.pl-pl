---
title: Wyjątki środowiska uruchomieniowego w aplikacjach .NET Native
ms.date: 03/30/2017
ms.assetid: 5f050181-8fdd-4a4e-9d16-f84c22a88a97
ms.openlocfilehash: 3132e2c9502c91cbfa0b120f664fd0c6f99a2663
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128143"
---
# <a name="runtime-exceptions-in-net-native-apps"></a><span data-ttu-id="7fa81-102">Wyjątki środowiska uruchomieniowego w aplikacjach .NET Native</span><span class="sxs-lookup"><span data-stu-id="7fa81-102">Runtime Exceptions in .NET Native Apps</span></span>
<span data-ttu-id="7fa81-103">Ważne jest, aby przetestować kompilacje wydań aplikacji platforma uniwersalna systemu Windows na swoich platformach docelowych, ponieważ konfiguracje debugowania i wydań są całkowicie różne.</span><span class="sxs-lookup"><span data-stu-id="7fa81-103">It is important to test the release builds of your Universal Windows Platform app on their target platforms because the debug and release configurations are completely different.</span></span> <span data-ttu-id="7fa81-104">Domyślnie Konfiguracja debugowania używa środowiska uruchomieniowego .NET Core do kompilowania aplikacji, ale konfiguracja wydania używa .NET Native do kompilowania aplikacji do kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="7fa81-104">By default, the debug configuration uses the .NET Core runtime to compile your app, but the release configuration uses .NET Native to compile your app to native code.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="7fa81-105">Aby uzyskać informacje na temat postępowania z wyjątkami [MissingMetadataException](missingmetadataexception-class-net-native.md), [MissingInteropDataException](missinginteropdataexception-class-net-native.md)i [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) , które mogą wystąpić podczas testowania wersji aplikacji, zobacz sekcję "krok 4: Ręcznie Rozwiązuj brakujące metadane: w temacie [wprowadzenie](getting-started-with-net-native.md) , a także informacje dotyczące [odbicia i .NET Native](reflection-and-net-native.md) i [środowiska uruchomieniowego dyrektywy (RD. xml)](runtime-directives-rd-xml-configuration-file-reference.md).</span><span class="sxs-lookup"><span data-stu-id="7fa81-105">For information on dealing with the [MissingMetadataException](missingmetadataexception-class-net-native.md), [MissingInteropDataException](missinginteropdataexception-class-net-native.md), and [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) exceptions that you may encounter when testing the release versions of your app, see "Step 4: Manually resolve missing metadata: in the [Getting Started](getting-started-with-net-native.md) topic, as well as [Reflection and .NET Native](reflection-and-net-native.md) and [Runtime Directives (rd.xml) Configuration File Reference](runtime-directives-rd-xml-configuration-file-reference.md).</span></span>  
  
## <a name="debug-and-release-builds"></a><span data-ttu-id="7fa81-106">Kompilacje debugowania i wydania</span><span class="sxs-lookup"><span data-stu-id="7fa81-106">Debug and release builds</span></span>  
 <span data-ttu-id="7fa81-107">Gdy Kompilacja debugowania jest wykonywana w środowisku uruchomieniowym .NET Core, nie została skompilowana do kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="7fa81-107">When the debug build executes against the .NET Core runtime, it has not been compiled to native code.</span></span> <span data-ttu-id="7fa81-108">Dzięki temu wszystkie usługi zwykle dostarczane przez środowisko uruchomieniowe są dostępne dla Twojej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7fa81-108">This makes all of the services ordinarily provided by the runtime available to your app.</span></span>  
  
 <span data-ttu-id="7fa81-109">Z drugiej strony Kompilacja wydania kompiluje się do kodu natywnego dla platform docelowych, usuwa większość zależności od zewnętrznych środowisk uruchomieniowych i bibliotek i intensywnie optymalizuje kod pod kątem maksymalnej wydajności.</span><span class="sxs-lookup"><span data-stu-id="7fa81-109">On the other hand, the release build compiles to native code for its target platforms, removes most dependencies on external runtimes and libraries, and heavily optimizes code for maximum performance.</span></span>  
  
 <span data-ttu-id="7fa81-110">Gdy debugujesz kompilacje wydań, które są kompilowane przy użyciu .NET Native:</span><span class="sxs-lookup"><span data-stu-id="7fa81-110">When you debug release builds that are compiled by using .NET Native:</span></span>  
  
- <span data-ttu-id="7fa81-111">Używasz aparatu debugowania .NET Native, który różni się od normalnych narzędzi debugowania platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="7fa81-111">You use the .NET Native debug engine, which is different from the normal .NET debugging tools.</span></span>  
  
- <span data-ttu-id="7fa81-112">Rozmiar pliku wykonywalnego jest krótszy, jak to możliwe.</span><span class="sxs-lookup"><span data-stu-id="7fa81-112">The size of your executable is reduced as much as possible.</span></span> <span data-ttu-id="7fa81-113">Jednym ze sposobów, który .NET Native zmniejsza rozmiar pliku wykonywalnego, jest znacznie przycinanie komunikatów o wyjątkach środowiska uruchomieniowego, temat opisany szczegółowo w sekcji [komunikaty o wyjątkach czasu wykonywania](#Messages) .</span><span class="sxs-lookup"><span data-stu-id="7fa81-113">One of the ways that .NET Native reduces the size of an executable is by significantly trimming runtime exception messages, a topic discussed in greater detail in the [Runtime exception messages](#Messages) section.</span></span>  
  
- <span data-ttu-id="7fa81-114">Kod jest silnie zoptymalizowany.</span><span class="sxs-lookup"><span data-stu-id="7fa81-114">Your code is heavily optimized.</span></span> <span data-ttu-id="7fa81-115">Oznacza to, że użycie funkcji tworzenia konspektu jest zawsze możliwe.</span><span class="sxs-lookup"><span data-stu-id="7fa81-115">This means that inlining is used whenever possible.</span></span> <span data-ttu-id="7fa81-116">(Odkreślenie przenosi kod z procedur zewnętrznych do procedury wywołującej).   Fakt, że .NET Native zapewnia wyspecjalizowane środowisko uruchomieniowe i implementuje agresywne wywołanie funkcji, która jest wyświetlana podczas debugowania.</span><span class="sxs-lookup"><span data-stu-id="7fa81-116">(Inlining moves code from external routines into the calling routine.)   The fact that .NET Native provides a specialized runtime and implements aggressive inlining  affects the call stack that is displayed when debugging.</span></span>  <span data-ttu-id="7fa81-117">Aby uzyskać więcej informacji, zobacz sekcję [stosu wywołań środowiska uruchomieniowego](#CallStack) .</span><span class="sxs-lookup"><span data-stu-id="7fa81-117">For more information, see the [Runtime call stack](#CallStack) section.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7fa81-118">Można kontrolować, czy kompilacje i wersje kompilacji są kompilowane za pomocą łańcucha narzędzi .NET Native, zaznaczając lub usuwając zaznaczenie pola wyboru **Kompiluj z .NET Native** .</span><span class="sxs-lookup"><span data-stu-id="7fa81-118">You can control whether the debug and release builds are compiled with the .NET Native tool chain by checking or unchecking the **Compile with .NET Native tool chain** box.</span></span>   <span data-ttu-id="7fa81-119">Należy jednak pamiętać, że Sklep Windows zawsze kompiluje wersję produkcyjną aplikacji za pomocą łańcucha narzędzi .NET Native.</span><span class="sxs-lookup"><span data-stu-id="7fa81-119">Note, however, that the Windows Store will always compile the production version of your app with the .NET Native tool chain.</span></span>  
  
<a name="Messages"></a>   
## <a name="runtime-exception-messages"></a><span data-ttu-id="7fa81-120">Komunikaty o wyjątkach środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="7fa81-120">Runtime exception messages</span></span>  
 <span data-ttu-id="7fa81-121">Aby zminimalizować rozmiar pliku wykonywalnego aplikacji, .NET Native nie zawiera pełnego tekstu komunikatów o wyjątkach.</span><span class="sxs-lookup"><span data-stu-id="7fa81-121">To minimize application executable size, .NET Native does not include the full text of exception messages.</span></span> <span data-ttu-id="7fa81-122">W związku z tym wyjątki środowiska uruchomieniowego zgłoszone w kompilacjach wydania mogą nie wyświetlać pełnego tekstu komunikatów o wyjątkach.</span><span class="sxs-lookup"><span data-stu-id="7fa81-122">As a result, runtime exceptions thrown in release builds may not display the full text of exception messages.</span></span> <span data-ttu-id="7fa81-123">Zamiast tego tekst może składać się z podciągu wraz z linkiem do kolejnych informacji.</span><span class="sxs-lookup"><span data-stu-id="7fa81-123">Instead, the text may consist of a substring along with a link to follow for more information.</span></span> <span data-ttu-id="7fa81-124">Na przykład informacje o wyjątku mogą wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="7fa81-124">For example, the exception information may appear as:</span></span>  
  
```output
Exception thrown: '$16_System.AggregateException' in Unknown Module.  
  
Additional information: AggregateException_ctor_DefaultMessage  
  
If there is a handler for this exception, the program may be safely continued.  
```  
  
 <span data-ttu-id="7fa81-125">Jeśli potrzebujesz pełnego komunikatu o wyjątku, zamiast tego Uruchom kompilację debugowania.</span><span class="sxs-lookup"><span data-stu-id="7fa81-125">If you need the complete exception message,  run the debug build instead.</span></span> <span data-ttu-id="7fa81-126">Na przykład poprzednie informacje o wyjątku z kompilacji wydania mogą pojawić się w następujący sposób w kompilacji debugowania:</span><span class="sxs-lookup"><span data-stu-id="7fa81-126">For example, the previous exception information  from the release build might appear as follows in the debug build:</span></span>  
  
```output
Exception thrown: 'System.AggregateException' in NativeApp.exe.  
  
Additional information: Value does not fall within the expected range.  
```  
  
<a name="CallStack"></a>   
## <a name="runtime-call-stack"></a><span data-ttu-id="7fa81-127">Stos wywołań środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="7fa81-127">Runtime call stack</span></span>  
 <span data-ttu-id="7fa81-128">Ze względu na niepodkreślanie i inne optymalizacje stos wywołań wyświetlany przez aplikację skompilowaną przez łańcuch narzędzi .NET Native może nie pomóc w jasno określić ścieżki do wyjątku czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="7fa81-128">Because of inlining and other optimizations, the call stack displayed by an app compiled by the .NET Native tool chain may not help you to  clearly identify the path to a runtime exception.</span></span>  
  
 <span data-ttu-id="7fa81-129">Aby uzyskać pełny stos, zamiast tego Uruchom kompilację debugowania.</span><span class="sxs-lookup"><span data-stu-id="7fa81-129">To get the full stack, run the debug build instead.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7fa81-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7fa81-130">See also</span></span>

- [<span data-ttu-id="7fa81-131">Debugowanie .NET Native uniwersalnych aplikacji systemu Windows</span><span class="sxs-lookup"><span data-stu-id="7fa81-131">Debugging .NET Native Windows Universal Apps</span></span>](https://devblogs.microsoft.com/devops/debugging-net-native-windows-universal-apps/)
- [<span data-ttu-id="7fa81-132">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="7fa81-132">Getting Started</span></span>](getting-started-with-net-native.md)

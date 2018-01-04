---
title: "Wyjątki czasu wykonywania w natywnych aplikacji .NET"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5f050181-8fdd-4a4e-9d16-f84c22a88a97
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cea4901eca45a4b02e3eeb9fa8a3ac2a9efa3484
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="runtime-exceptions-in-net-native-apps"></a><span data-ttu-id="4a9c2-102">Wyjątki czasu wykonywania w natywnych aplikacji .NET</span><span class="sxs-lookup"><span data-stu-id="4a9c2-102">Runtime Exceptions in .NET Native Apps</span></span>
<span data-ttu-id="4a9c2-103">Należy koniecznie test kompilacjami wydania aplikacji platformy uniwersalnej systemu Windows na ich platformach docelowych, ponieważ są całkowicie różne konfiguracje debug i release.</span><span class="sxs-lookup"><span data-stu-id="4a9c2-103">It is important to test the release builds of your Universal Windows Platform app on their target platforms because the debug and release configurations are completely different.</span></span> <span data-ttu-id="4a9c2-104">Domyślnie korzysta z konfiguracji debugowania środowiska uruchomieniowego .NET Core do skompilowania aplikacji, ale konfiguracja wydania używają platformy .NET Native skompilować aplikację do kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="4a9c2-104">By default, the debug configuration uses the .NET Core runtime to compile your app, but the release configuration uses .NET Native to compile your app to native code.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="4a9c2-105">Aby uzyskać informacje o obsłudze [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md), [MissingInteropDataException](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md), i [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) wyjątki, które możesz Podczas testowania wersji aplikacji, zobacz "krok 4: ręcznie rozwiązać Brak metadanych: w [wprowadzenie](../../../docs/framework/net-native/getting-started-with-net-native.md) tematu, jak również [odbicie i architektura .NET Native](../../../docs/framework/net-native/reflection-and-net-native.md) i [ Odwołanie do pliku konfiguracji dyrektyw (rd.xml) środowiska uruchomieniowego](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md).</span><span class="sxs-lookup"><span data-stu-id="4a9c2-105">For information on dealing with the [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md), [MissingInteropDataException](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md), and [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) exceptions that you may encounter when testing the release versions of your app, see  "Step 4: Manually resolve missing metadata: in the [Getting Started](../../../docs/framework/net-native/getting-started-with-net-native.md) topic, as well as [Reflection and .NET Native](../../../docs/framework/net-native/reflection-and-net-native.md) and [Runtime Directives (rd.xml) Configuration File Reference](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md).</span></span>  
  
## <a name="debug-and-release-builds"></a><span data-ttu-id="4a9c2-106">Kompilacje debugowania i wydania</span><span class="sxs-lookup"><span data-stu-id="4a9c2-106">Debug and release builds</span></span>  
 <span data-ttu-id="4a9c2-107">Podczas kompilacji debugowania dla środowiska uruchomieniowego .NET Core, nie ma została skompilowana do kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="4a9c2-107">When the debug build executes against the .NET Core runtime, it has not been compiled to native code.</span></span> <span data-ttu-id="4a9c2-108">Spowoduje to uruchomienie wszystkich usług, zwykle dostarczonym w czasie wykonywania, dostępne dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4a9c2-108">This makes all of the services ordinarily provided by the runtime available to your app.</span></span>  
  
 <span data-ttu-id="4a9c2-109">Z drugiej strony kompilacji wydania kompiluje się do kodu natywnego dla jego platformy docelowe, powoduje usunięcie większości zależności zewnętrznych środowisk uruchomieniowych i bibliotek i silnie optymalizuje kod dla maksymalnej wydajności.</span><span class="sxs-lookup"><span data-stu-id="4a9c2-109">On the other hand, the release build compiles to native code for its target platforms, removes most dependencies on external runtimes and libraries, and heavily optimizes code for maximum performance.</span></span>  
  
 <span data-ttu-id="4a9c2-110">Podczas debugowania kompilacjami wydania, które są kompilowane przy użyciu platformy .NET Native:</span><span class="sxs-lookup"><span data-stu-id="4a9c2-110">When you debug release builds that are compiled by using .NET Native:</span></span>  
  
-   <span data-ttu-id="4a9c2-111">Używasz platformy .NET Native aparat debugowania, który różni się od normalnego narzędzia debugowania środowiska .NET.</span><span class="sxs-lookup"><span data-stu-id="4a9c2-111">You use the .NET Native debug engine, which is different from the normal .NET debugging tools.</span></span>  
  
-   <span data-ttu-id="4a9c2-112">Rozmiar pliku wykonywalnego zmniejsza się w miarę możliwości.</span><span class="sxs-lookup"><span data-stu-id="4a9c2-112">The size of your executable is reduced as much as possible.</span></span> <span data-ttu-id="4a9c2-113">Jednym ze sposobów platformy .NET Native zmniejsza rozmiar pliku wykonywalnego jest znacznie przycinanie komunikaty o wyjątkach środowiska uruchomieniowego, temacie omówiono bardziej szczegółowo w [komunikaty o wyjątkach środowiska uruchomieniowego](#Messages) sekcji.</span><span class="sxs-lookup"><span data-stu-id="4a9c2-113">One of the ways that .NET Native reduces the size of an executable is by significantly trimming runtime exception messages, a topic discussed in greater detail in the [Runtime exception messages](#Messages) section.</span></span>  
  
-   <span data-ttu-id="4a9c2-114">Kod silnie jest zoptymalizowany.</span><span class="sxs-lookup"><span data-stu-id="4a9c2-114">Your code is heavily optimized.</span></span> <span data-ttu-id="4a9c2-115">Oznacza to, że ze śródwierszowaniem jest używany, gdy jest to możliwe.</span><span class="sxs-lookup"><span data-stu-id="4a9c2-115">This means that inlining is used whenever possible.</span></span> <span data-ttu-id="4a9c2-116">(Ze Śródwierszowaniem przenosi kodu z zewnętrznej procedury do wywoływania procedury.)   Fakt, że platforma .NET Native zawiera specjalne środowiska uruchomieniowego i implementuje agresywne ze śródwierszowaniem wpływa na stos wywołań, który jest wyświetlany podczas debugowania.</span><span class="sxs-lookup"><span data-stu-id="4a9c2-116">(Inlining moves code from external routines into the calling routine.)   The fact that .NET Native provides a specialized runtime and implements aggressive inlining  affects the call stack that is displayed when debugging.</span></span>  <span data-ttu-id="4a9c2-117">Aby uzyskać więcej informacji, zobacz [stosu wywołań środowiska uruchomieniowego](#CallStack) sekcji.</span><span class="sxs-lookup"><span data-stu-id="4a9c2-117">For more information, see the [Runtime call stack](#CallStack) section.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4a9c2-118">Można kontrolować, czy kompilacji debug i release są kompilowane przy użyciu platformy .NET Native łańcucha narzędzi przez zaznaczenie lub usunięcie zaznaczenia **Kompiluj z użyciem łańcucha narzędzi dla platformy .NET Native** pole.</span><span class="sxs-lookup"><span data-stu-id="4a9c2-118">You can control whether the debug and release builds are compiled with the .NET Native tool chain by checking or unchecking the **Compile with .NET Native tool chain** box.</span></span>   <span data-ttu-id="4a9c2-119">Należy jednak pamiętać, że Sklep Windows zawsze zostanie skompilowany wersji produkcyjnej aplikacji z użyciem platformy .NET Native łańcucha narzędzi.</span><span class="sxs-lookup"><span data-stu-id="4a9c2-119">Note, however, that the Windows Store will always compile the production version of your app with the .NET Native tool chain.</span></span>  
  
<a name="Messages"></a>   
## <a name="runtime-exception-messages"></a><span data-ttu-id="4a9c2-120">Komunikaty o wyjątkach środowiska wykonawczego</span><span class="sxs-lookup"><span data-stu-id="4a9c2-120">Runtime exception messages</span></span>  
 <span data-ttu-id="4a9c2-121">Aby zminimalizować rozmiar pliku wykonywalnego aplikacji, platformy .NET Native nie obejmuje pełny tekst komunikaty o wyjątku.</span><span class="sxs-lookup"><span data-stu-id="4a9c2-121">To minimize application executable size, .NET Native does not include the full text of exception messages.</span></span> <span data-ttu-id="4a9c2-122">W związku z tym obsługi wyjątków zgłoszonych w kompilacjach wydania nie może być wyświetlany pełny tekst komunikaty o wyjątku.</span><span class="sxs-lookup"><span data-stu-id="4a9c2-122">As a result, runtime exceptions thrown in release builds may not display the full text of exception messages.</span></span> <span data-ttu-id="4a9c2-123">Zamiast tego tekst może zawierać podciąg wraz z linkiem, które należy wykonać, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="4a9c2-123">Instead, the text may consist of a substring along with a link to follow for more information.</span></span> <span data-ttu-id="4a9c2-124">Na przykład informacje o wyjątku może pojawić się jako:</span><span class="sxs-lookup"><span data-stu-id="4a9c2-124">For example, the exception information may appear as:</span></span>  
  
```  
Exception thrown: '$16_System.AggregateException' in Unknown Module.  
  
Additional information: AggregateException_ctor_DefaultMessage  
  
If there is a handler for this exception, the program may be safely continued.  
```  
  
 <span data-ttu-id="4a9c2-125">Komunikat o wyjątku pełnej, należy należy uruchomić z kompilacji debugowania.</span><span class="sxs-lookup"><span data-stu-id="4a9c2-125">If you need the complete exception message,  run the debug build instead.</span></span> <span data-ttu-id="4a9c2-126">Na przykład informacje o poprzednich wyjątku z kompilacji wydania mogą wyglądać następująco w kompilacji debugowania:</span><span class="sxs-lookup"><span data-stu-id="4a9c2-126">For example, the previous exception information  from the release build might appear as follows in the debug build:</span></span>  
  
```  
Exception thrown: 'System.AggregateException' in NativeApp.exe.  
  
Additional information: Value does not fall within the expected range.  
```  
  
<a name="CallStack"></a>   
## <a name="runtime-call-stack"></a><span data-ttu-id="4a9c2-127">Stos wywołań środowiska wykonawczego</span><span class="sxs-lookup"><span data-stu-id="4a9c2-127">Runtime call stack</span></span>  
 <span data-ttu-id="4a9c2-128">Z powodu optymalizacji ze śródwierszowaniem i innych stos wywołań, wyświetlane przez aplikację skompilowane przez platformę .NET Native łańcucha narzędzi może nie pomóc w celu jednoznacznego zidentyfikowania ścieżkę do wyjątek czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="4a9c2-128">Because of inlining and other optimizations, the call stack displayed by an app compiled by the .NET Native tool chain may not help you to  clearly identify the path to a runtime exception.</span></span>  
  
 <span data-ttu-id="4a9c2-129">Aby uzyskać pełne stosu, należy uruchomić kompilacji debugowania.</span><span class="sxs-lookup"><span data-stu-id="4a9c2-129">To get the full stack, run the debug build instead.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a9c2-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4a9c2-130">See Also</span></span>  
 [<span data-ttu-id="4a9c2-131">Debugowania .NET Native uniwersalnych aplikacji systemu Windows</span><span class="sxs-lookup"><span data-stu-id="4a9c2-131">Debugging .NET Native Windows Universal Apps</span></span>](http://blogs.msdn.com/b/visualstudioalm/archive/2015/07/29/debugging-net-native-windows-universal-apps.aspx)  
 [<span data-ttu-id="4a9c2-132">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="4a9c2-132">Getting Started</span></span>](../../../docs/framework/net-native/getting-started-with-net-native.md)

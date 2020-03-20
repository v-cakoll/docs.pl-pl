---
title: Wyjątki środowiska uruchomieniowego w aplikacjach .NET Native
ms.date: 03/30/2017
ms.assetid: 5f050181-8fdd-4a4e-9d16-f84c22a88a97
ms.openlocfilehash: 12df2ef7bf6e86a60dfa4c130f35969e72ac5211
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180947"
---
# <a name="runtime-exceptions-in-net-native-apps"></a><span data-ttu-id="38362-102">Wyjątki środowiska uruchomieniowego w aplikacjach .NET Native</span><span class="sxs-lookup"><span data-stu-id="38362-102">Runtime Exceptions in .NET Native Apps</span></span>
<span data-ttu-id="38362-103">Ważne jest, aby przetestować kompilacje wersji aplikacji platformy uniwersalnej systemu Windows na ich platformach docelowych, ponieważ konfiguracje debugowania i wydania są zupełnie inne.</span><span class="sxs-lookup"><span data-stu-id="38362-103">It is important to test the release builds of your Universal Windows Platform app on their target platforms because the debug and release configurations are completely different.</span></span> <span data-ttu-id="38362-104">Domyślnie konfiguracja debugowania używa środowiska uruchomieniowego .NET Core do skompilowania aplikacji, ale konfiguracja wersji używa platformy .NET Native do skompilowania aplikacji z kodem macierzystym.</span><span class="sxs-lookup"><span data-stu-id="38362-104">By default, the debug configuration uses the .NET Core runtime to compile your app, but the release configuration uses .NET Native to compile your app to native code.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="38362-105">Aby uzyskać informacje na temat radzenia sobie z [missingmetadataException](missingmetadataexception-class-net-native.md), [MissingInteropDataException](missinginteropdataexception-class-net-native.md)i [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) wyjątki, które można napotkać podczas testowania wersji aplikacji, zobacz "Krok 4: Ręczne rozwiązywanie brakujących metadanych: w temacie [Wprowadzenie,](getting-started-with-net-native.md) a także [odbicie i .NET Natywne](reflection-and-net-native.md) i [runtime dyrektywy (rd.xml) Odwołanie do pliku konfiguracyjnego](runtime-directives-rd-xml-configuration-file-reference.md).</span><span class="sxs-lookup"><span data-stu-id="38362-105">For information on dealing with the [MissingMetadataException](missingmetadataexception-class-net-native.md), [MissingInteropDataException](missinginteropdataexception-class-net-native.md), and [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) exceptions that you may encounter when testing the release versions of your app, see "Step 4: Manually resolve missing metadata: in the [Getting Started](getting-started-with-net-native.md) topic, as well as [Reflection and .NET Native](reflection-and-net-native.md) and [Runtime Directives (rd.xml) Configuration File Reference](runtime-directives-rd-xml-configuration-file-reference.md).</span></span>  
  
## <a name="debug-and-release-builds"></a><span data-ttu-id="38362-106">Debugowanie i wydawanie kompilacji</span><span class="sxs-lookup"><span data-stu-id="38362-106">Debug and release builds</span></span>  
 <span data-ttu-id="38362-107">Gdy kompilacja debugowania jest wykonywana względem środowiska uruchomieniowego .NET Core, nie została skompilowana do kodu macierzystego.</span><span class="sxs-lookup"><span data-stu-id="38362-107">When the debug build executes against the .NET Core runtime, it has not been compiled to native code.</span></span> <span data-ttu-id="38362-108">Dzięki temu wszystkie usługi zwykle dostarczane przez środowisko wykonawcze są dostępne dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="38362-108">This makes all of the services ordinarily provided by the runtime available to your app.</span></span>  
  
 <span data-ttu-id="38362-109">Z drugiej strony kompilacja wydania kompiluje do kodu macierzystego dla swoich platform docelowych, usuwa większość zależności w zewnętrznych środowiskach uruchomieniowych i bibliotekach i mocno optymalizuje kod pod kątem maksymalnej wydajności.</span><span class="sxs-lookup"><span data-stu-id="38362-109">On the other hand, the release build compiles to native code for its target platforms, removes most dependencies on external runtimes and libraries, and heavily optimizes code for maximum performance.</span></span>  
  
 <span data-ttu-id="38362-110">Podczas debugowania kompilacji wydania, które są kompilowane przy użyciu platformy .NET Native:</span><span class="sxs-lookup"><span data-stu-id="38362-110">When you debug release builds that are compiled by using .NET Native:</span></span>  
  
- <span data-ttu-id="38362-111">Aparat debugowania natywnego platformy .NET różni się od zwykłych narzędzi debugowania platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="38362-111">You use the .NET Native debug engine, which is different from the normal .NET debugging tools.</span></span>  
  
- <span data-ttu-id="38362-112">Rozmiar pliku wykonywalnego jest zmniejszany w miarę możliwości.</span><span class="sxs-lookup"><span data-stu-id="38362-112">The size of your executable is reduced as much as possible.</span></span> <span data-ttu-id="38362-113">Jednym ze sposobów, że .NET Native zmniejsza rozmiar pliku wykonywalnego jest znacznie przycinanie komunikatów wyjątków środowiska uruchomieniowego, temat omówione bardziej szczegółowo w sekcji [Komunikaty wyjątków środowiska wykonawczego.](#Messages)</span><span class="sxs-lookup"><span data-stu-id="38362-113">One of the ways that .NET Native reduces the size of an executable is by significantly trimming runtime exception messages, a topic discussed in greater detail in the [Runtime exception messages](#Messages) section.</span></span>  
  
- <span data-ttu-id="38362-114">Kod jest mocno zoptymalizowany.</span><span class="sxs-lookup"><span data-stu-id="38362-114">Your code is heavily optimized.</span></span> <span data-ttu-id="38362-115">Oznacza to, że inline jest używany, gdy jest to możliwe.</span><span class="sxs-lookup"><span data-stu-id="38362-115">This means that inlining is used whenever possible.</span></span> <span data-ttu-id="38362-116">(Inlining przenosi kod z procedur zewnętrznych do procedury wywoływania).   Fakt, że .NET Native zapewnia wyspecjalizowane środowisko uruchomieniowe i implementuje agresywne inline wpływa na stos wywołań, który jest wyświetlany podczas debugowania.</span><span class="sxs-lookup"><span data-stu-id="38362-116">(Inlining moves code from external routines into the calling routine.)   The fact that .NET Native provides a specialized runtime and implements aggressive inlining  affects the call stack that is displayed when debugging.</span></span>  <span data-ttu-id="38362-117">Aby uzyskać więcej informacji, zobacz [runtime call stack](#CallStack) sekcji.</span><span class="sxs-lookup"><span data-stu-id="38362-117">For more information, see the [Runtime call stack](#CallStack) section.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="38362-118">Można kontrolować, czy kompilacje debugowania i wydania są kompilowane za pomocą łańcucha narzędzi natywnych platformy .NET, zaznaczając lub odznaczając pole **łańcucha narzędzi Kompilacja za pomocą narzędzia .NET Native.**</span><span class="sxs-lookup"><span data-stu-id="38362-118">You can control whether the debug and release builds are compiled with the .NET Native tool chain by checking or unchecking the **Compile with .NET Native tool chain** box.</span></span>   <span data-ttu-id="38362-119">Należy jednak pamiętać, że Sklep Windows zawsze skompiluje wersję produkcyjną aplikacji z łańcuchem narzędzi natywnych dla platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="38362-119">Note, however, that the Windows Store will always compile the production version of your app with the .NET Native tool chain.</span></span>  
  
<a name="Messages"></a>
## <a name="runtime-exception-messages"></a><span data-ttu-id="38362-120">Komunikaty o wyjątkach środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="38362-120">Runtime exception messages</span></span>  
 <span data-ttu-id="38362-121">Aby zminimalizować rozmiar pliku wykonywalnego aplikacji, .NET Native nie zawiera pełnego tekstu komunikatów wyjątków.</span><span class="sxs-lookup"><span data-stu-id="38362-121">To minimize application executable size, .NET Native does not include the full text of exception messages.</span></span> <span data-ttu-id="38362-122">W rezultacie wyjątki środowiska uruchomieniowego zgłaszane w kompilacjach wydania mogą nie wyświetlać pełnego tekstu komunikatów wyjątków.</span><span class="sxs-lookup"><span data-stu-id="38362-122">As a result, runtime exceptions thrown in release builds may not display the full text of exception messages.</span></span> <span data-ttu-id="38362-123">Zamiast tego tekst może składać się z podciągów wraz z linkiem do naśladowania, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="38362-123">Instead, the text may consist of a substring along with a link to follow for more information.</span></span> <span data-ttu-id="38362-124">Na przykład informacje o wyjątku mogą być wyświetlane jako:</span><span class="sxs-lookup"><span data-stu-id="38362-124">For example, the exception information may appear as:</span></span>  
  
```output
Exception thrown: '$16_System.AggregateException' in Unknown Module.  
  
Additional information: AggregateException_ctor_DefaultMessage  
  
If there is a handler for this exception, the program may be safely continued.  
```  
  
 <span data-ttu-id="38362-125">Jeśli potrzebujesz komunikatu o pełnym wyjątku, uruchom zamiast tego kompilację debugowania.</span><span class="sxs-lookup"><span data-stu-id="38362-125">If you need the complete exception message,  run the debug build instead.</span></span> <span data-ttu-id="38362-126">Na przykład poprzednie informacje o wyjątku z kompilacji wydania mogą być wyświetlane w następujący sposób w kompilacji debugowania:</span><span class="sxs-lookup"><span data-stu-id="38362-126">For example, the previous exception information  from the release build might appear as follows in the debug build:</span></span>  
  
```output
Exception thrown: 'System.AggregateException' in NativeApp.exe.  
  
Additional information: Value does not fall within the expected range.  
```  
  
<a name="CallStack"></a>
## <a name="runtime-call-stack"></a><span data-ttu-id="38362-127">Stos wywołań środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="38362-127">Runtime call stack</span></span>  
 <span data-ttu-id="38362-128">Ze względu na inline i innych optymalizacji stos wywołań wyświetlany przez aplikację skompilowaną przez łańcuch narzędzi natywnych platformy .NET może nie pomóc w jasnych identyfikowaniu ścieżki do wyjątku środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="38362-128">Because of inlining and other optimizations, the call stack displayed by an app compiled by the .NET Native tool chain may not help you to  clearly identify the path to a runtime exception.</span></span>  
  
 <span data-ttu-id="38362-129">Aby uzyskać pełny stos, uruchom kompilację debugowania zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="38362-129">To get the full stack, run the debug build instead.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38362-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="38362-130">See also</span></span>

- [<span data-ttu-id="38362-131">Debugowanie natywnych aplikacji systemu Windows .NET</span><span class="sxs-lookup"><span data-stu-id="38362-131">Debugging .NET Native Windows Universal Apps</span></span>](https://devblogs.microsoft.com/devops/debugging-net-native-windows-universal-apps/)
- [<span data-ttu-id="38362-132">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="38362-132">Getting Started</span></span>](getting-started-with-net-native.md)

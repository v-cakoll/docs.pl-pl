---
title: Analizatory zabezpieczeń .NET — .NET
description: Dowiedz się, jak używane analizatory zabezpieczeń .NET pakietu .NET Framework analizatorów, aby zidentyfikować i rozwiązać zagrożenia bezpieczeństwa
author: billwagner
ms.author: wiwagn
ms.date: 01/25/2018
ms.technology: dotnet-standard
ms.openlocfilehash: cbd9bcdb12a423f54aa4ff82d88f07c20023c48f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59197656"
---
# <a name="the-net-framework-analyzer"></a><span data-ttu-id="5d267-103">Analizator struktury platformy .NET</span><span class="sxs-lookup"><span data-stu-id="5d267-103">The .NET Framework Analyzer</span></span>

<span data-ttu-id="5d267-104">Analizator struktury platformy .NET umożliwia znalezienie potencjalnych problemów w kodzie aplikacji opartych na programie .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5d267-104">You can use the .NET Framework Analyzer to find potential issues in your .NET Framework-based application code.</span></span> <span data-ttu-id="5d267-105">Ten analizatora umożliwia znalezienie potencjalnych problemów i sugeruje poprawki do nich.</span><span class="sxs-lookup"><span data-stu-id="5d267-105">This analyzer finds potential issues and suggests fixes to them.</span></span>

<span data-ttu-id="5d267-106">Analizator działa interaktywnie w programie Visual Studio podczas pisania kodu lub jako część kompilacji ciągłej integracji.</span><span class="sxs-lookup"><span data-stu-id="5d267-106">The analyzer runs interactively in Visual Studio as you write your code or as part of a CI build.</span></span> <span data-ttu-id="5d267-107">Tworzenie, należy dodać analizatora możliwie jak najszybciej do projektu.</span><span class="sxs-lookup"><span data-stu-id="5d267-107">You should add the analyzer to your project as early as possible in your development.</span></span> <span data-ttu-id="5d267-108">Szybciej znaleźć potencjalnych problemów w kodzie, tym łatwiej są Aby rozwiązać problem.</span><span class="sxs-lookup"><span data-stu-id="5d267-108">The sooner you find any potential issues in your code, the easier they are to fix.</span></span> <span data-ttu-id="5d267-109">Jednak można go dodać w dowolnym momencie w cyklu rozwoju.</span><span class="sxs-lookup"><span data-stu-id="5d267-109">However, you can add it at any time in the development cycle.</span></span> <span data-ttu-id="5d267-110">Znajdzie wszystkie problemy z istniejącego kodu i ostrzega o nowych problemach, jak zachować opracowywania.</span><span class="sxs-lookup"><span data-stu-id="5d267-110">It finds any issues with the existing code and warns about new issues as you keep developing.</span></span>

## <a name="installing-and-configuring-the-net-framework-analyzer"></a><span data-ttu-id="5d267-111">Instalowanie i konfigurowanie analizator struktury platformy .NET</span><span class="sxs-lookup"><span data-stu-id="5d267-111">Installing and configuring the .NET Framework Analyzer</span></span>

<span data-ttu-id="5d267-112">Analizatory zabezpieczeń .NET musi być zainstalowany jako pakiet NuGet w projekcie, co potrzebne do uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="5d267-112">The .NET Security Analyzers must be installed as a NuGet package on every project where you want them to run.</span></span> <span data-ttu-id="5d267-113">Tylko jeden deweloper musi zostać dodane do projektu.</span><span class="sxs-lookup"><span data-stu-id="5d267-113">Only one developer needs to add them to the project.</span></span> <span data-ttu-id="5d267-114">Pakiet analizatora jest zależnością projektu i zostanie uruchomiony na maszynie każdego dewelopera, gdy ma ona zaktualizowane rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="5d267-114">The analyzer package is a project dependency and will run on every developer's machine once it has the updated solution.</span></span>

<span data-ttu-id="5d267-115">Analizator struktury platformy .NET jest dostarczany za [Microsoft.NetFramework.Analyzers](https://www.nuget.org/packages/Microsoft.NetFramework.Analyzers/) pakietu NuGet.</span><span class="sxs-lookup"><span data-stu-id="5d267-115">The .NET Framework Analyzer is delivered in the [Microsoft.NetFramework.Analyzers](https://www.nuget.org/packages/Microsoft.NetFramework.Analyzers/) NuGet package.</span></span> <span data-ttu-id="5d267-116">Ten pakiet zawiera określone analizatory do programu .NET Framework, w tym analizatory zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="5d267-116">This package provides only the analyzers specific to the .NET Framework, which includes security analyzers.</span></span> <span data-ttu-id="5d267-117">W większości przypadków należy [Microsoft.CodeAnalysis.FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) pakietu NuGet.</span><span class="sxs-lookup"><span data-stu-id="5d267-117">In most cases, you'll want the [Microsoft.CodeAnalysis.FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) NuGet package.</span></span> <span data-ttu-id="5d267-118">Pakiet agregacji FxCopAnalyzers zawiera analizatorów framework zawarte w pakiecie Framework.Analyzers, jak również analizatory następujące:</span><span class="sxs-lookup"><span data-stu-id="5d267-118">The FxCopAnalyzers aggregate package contains all the framework analyzers included in the Framework.Analyzers package as well as the following analyzers:</span></span>
- <span data-ttu-id="5d267-119">[Microsoft.CodeQuality.Analyzers](https://www.nuget.org/packages/Microsoft.CodeQuality.Analyzers): Zawiera ogólne wskazówki i wskazówki dotyczące standardowych interfejsów API platformy .NET</span><span class="sxs-lookup"><span data-stu-id="5d267-119">[Microsoft.CodeQuality.Analyzers](https://www.nuget.org/packages/Microsoft.CodeQuality.Analyzers): Provides general guidance and guidance for .NET Standard APIs</span></span>
- <span data-ttu-id="5d267-120">[Microsoft.NetCore.Analyzers](https://www.nuget.org/packages/Microsoft.NetCore.Analyzers): Zapewnia analizatory określonych interfejsów API platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5d267-120">[Microsoft.NetCore.Analyzers](https://www.nuget.org/packages/Microsoft.NetCore.Analyzers): Provides analyzers specific to .NET Core APIs.</span></span>
- <span data-ttu-id="5d267-121">[Text.Analyzers](https://www.nuget.org/packages/Text.Analyzers): Zawiera wskazówki dotyczące tekst zawarty jako kodu, w tym komentarzy.</span><span class="sxs-lookup"><span data-stu-id="5d267-121">[Text.Analyzers](https://www.nuget.org/packages/Text.Analyzers): Provides guidance for text included as code, including comments.</span></span>

<span data-ttu-id="5d267-122">Aby go zainstalować, kliknij prawym przyciskiem myszy nad projektem i wybierz pozycję "Zarządzaj zależności".</span><span class="sxs-lookup"><span data-stu-id="5d267-122">To install it, right-click on the project, and select "Manage Dependencies".</span></span>
<span data-ttu-id="5d267-123">Z poziomu Eksploratora NuGet, wyszukaj "NetFramework analizatora", lub jeśli wolisz "Fx Cop analizatora".</span><span class="sxs-lookup"><span data-stu-id="5d267-123">From the NuGet explorer, search for "NetFramework Analyzer", or if you prefer, "Fx Cop Analyzer".</span></span> <span data-ttu-id="5d267-124">Zainstaluj najnowszą wersję stabilną we wszystkich projektach w rozwiązaniu.</span><span class="sxs-lookup"><span data-stu-id="5d267-124">Install the latest stable version in all projects in your solution.</span></span>

## <a name="using-the-net-framework-analyzer"></a><span data-ttu-id="5d267-125">Za pomocą analizatora .NET Framework</span><span class="sxs-lookup"><span data-stu-id="5d267-125">Using the .NET Framework Analyzer</span></span>

<span data-ttu-id="5d267-126">Po zainstalowaniu pakietu NuGet, Skompiluj rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="5d267-126">Once the NuGet package is installed, build your solution.</span></span> <span data-ttu-id="5d267-127">Analizator będzie zgłaszać problemy, które klient zlokalizuje w bazie kodu.</span><span class="sxs-lookup"><span data-stu-id="5d267-127">The analyzer will report any issues it locates in your codebase.</span></span> <span data-ttu-id="5d267-128">Problemy są zgłaszane jako ostrzeżenia w oknie Lista błędów w usłudze Visual Studio, jak pokazano na poniższej ilustracji:</span><span class="sxs-lookup"><span data-stu-id="5d267-128">The issues are reported as warnings in the Visual Studio Error List window, as shown in the following image:</span></span>

![problemów zgłaszanych przez analizator struktury](./media/framework-analyzers-2.png)

<span data-ttu-id="5d267-130">Podczas pisania kodu, zobaczysz zygzaki poniżej potencjalne problemy w kodzie.</span><span class="sxs-lookup"><span data-stu-id="5d267-130">As you write code, you see squiggles underneath any potential issue in your code.</span></span>
<span data-ttu-id="5d267-131">Umieść kursor nad dowolnym problemem i wyświetlić szczegółowe informacje o problemie i sugestie dotyczące wszystkie możliwe rozwiązanie, jak pokazano na poniższej ilustracji:</span><span class="sxs-lookup"><span data-stu-id="5d267-131">Hover over any issue and you see details about the issue, and suggestions for any possible fix, as shown in the following image:</span></span>

![interaktywny raport problemów wykrytych przez analizator struktury](./media/framework-analyzers-1.png)

<span data-ttu-id="5d267-133">Analizatorów sprawdzić kod w rozwiązaniu i udostępniać Ci listę ostrzeżeń dla każdego z tych problemów:</span><span class="sxs-lookup"><span data-stu-id="5d267-133">The analyzers examine the code in your solution and provide you with a list of warnings for any of these issues:</span></span>

### <a name="ca1058-types-should-not-extend-certain-base-types"></a><span data-ttu-id="5d267-134">CA1058: Typy nie powinny rozszerzać niektórych typów podstawowych</span><span class="sxs-lookup"><span data-stu-id="5d267-134">CA1058: Types should not extend certain base types</span></span>

<span data-ttu-id="5d267-135">Istnieje niewielka liczba typów w .NET Framework, należy nie pochodzi od bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="5d267-135">There are a small number of types in the .NET Framework that you should not derived from directly.</span></span> 

<span data-ttu-id="5d267-136">**Kategoria:** Projekt</span><span class="sxs-lookup"><span data-stu-id="5d267-136">**Category:** Design</span></span>

<span data-ttu-id="5d267-137">**Ważność:** Ostrzeżenie</span><span class="sxs-lookup"><span data-stu-id="5d267-137">**Severity:** Warning</span></span>

<span data-ttu-id="5d267-138">Informacje dodatkowe: [CA:1058: Typy nie powinny rozszerzać niektórych typów podstawowych](/visualstudio/code-quality/ca1058-types-should-not-extend-certain-base-types)</span><span class="sxs-lookup"><span data-stu-id="5d267-138">Additional information: [CA:1058: Types should not extend certain base types](/visualstudio/code-quality/ca1058-types-should-not-extend-certain-base-types)</span></span>

### <a name="ca2153-do-not-catch-corrupted-state-exceptions"></a><span data-ttu-id="5d267-139">CA2153: Nie przechwytuj wyjątki uszkodzony</span><span class="sxs-lookup"><span data-stu-id="5d267-139">CA2153: Do not catch corrupted state exceptions</span></span>

<span data-ttu-id="5d267-140">Połowowe wyjątki uszkodzony może maskować błędów (np. naruszenia zasad dostępu), co w niespójnym stanie wykonywania lub ułatwianie dla osób atakujących do naruszenia bezpieczeństwa systemu.</span><span class="sxs-lookup"><span data-stu-id="5d267-140">Catching corrupted state exceptions could mask errors (such as access violations), resulting in an inconsistent state of execution or making it easier for attackers to compromise a system.</span></span> <span data-ttu-id="5d267-141">Zamiast tego catch i zajmują więcej określony zestaw typów wyjątków lub ponownie zgłosić wyjątek</span><span class="sxs-lookup"><span data-stu-id="5d267-141">Instead, catch and handle a more specific set of exception type(s) or re-throw the exception</span></span>

<span data-ttu-id="5d267-142">**Kategoria:** Zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="5d267-142">**Category:** Security</span></span>

<span data-ttu-id="5d267-143">**Ważność:** Ostrzeżenie</span><span class="sxs-lookup"><span data-stu-id="5d267-143">**Severity:** Warning</span></span>

<span data-ttu-id="5d267-144">Informacje dodatkowe: [## CA2153: Nie przechwytuj wyjątki uszkodzony](/visualstudio/code-quality/ca2153-avoid-handling-corrupted-state-exceptions)</span><span class="sxs-lookup"><span data-stu-id="5d267-144">Additional information: [## CA2153: Do not catch corrupted state exceptions](/visualstudio/code-quality/ca2153-avoid-handling-corrupted-state-exceptions)</span></span>

### <a name="ca2229-implement-serialization-constructors"></a><span data-ttu-id="5d267-145">CA2229: Zaimplementuj konstruktory serializacji</span><span class="sxs-lookup"><span data-stu-id="5d267-145">CA2229: Implement serialization constructors</span></span>

<span data-ttu-id="5d267-146">Analizator generuje to ostrzeżenie, po utworzeniu typu, który implementuje <xref:System.Runtime.Serialization.ISerializable> interfejsu, ale nie definiuje konstruktora serializacji wymagane.</span><span class="sxs-lookup"><span data-stu-id="5d267-146">The analyzer generates this warning when you create a type that implements the <xref:System.Runtime.Serialization.ISerializable> interface but does not define the required serialization constructor.</span></span> <span data-ttu-id="5d267-147">Aby naprawić naruszenie tej zasady, należy zaimplementować konstruktora serializacji.</span><span class="sxs-lookup"><span data-stu-id="5d267-147">To fix a violation of this rule, implement the serialization constructor.</span></span> <span data-ttu-id="5d267-148">Dla zamkniętej klasy należy ustawić konstruktor prywatny; w przeciwnym razie powinien być chroniony.</span><span class="sxs-lookup"><span data-stu-id="5d267-148">For a sealed class, make the constructor private; otherwise, make it protected.</span></span> <span data-ttu-id="5d267-149">Konstruktor serializacji ma następujący podpis:</span><span class="sxs-lookup"><span data-stu-id="5d267-149">The serialization constructor has the following signature:</span></span>

```csharp
public class MyItemType
{
    // The special constructor is used to deserialize values.
    public MyItemType(SerializationInfo info, StreamingContext context)
    {
        // implementation removed.
    }
}
```

<span data-ttu-id="5d267-150">**Kategoria:** Użycie</span><span class="sxs-lookup"><span data-stu-id="5d267-150">**Category:** Usage</span></span>

<span data-ttu-id="5d267-151">**Ważność:** Ostrzeżenie</span><span class="sxs-lookup"><span data-stu-id="5d267-151">**Severity:** Warning</span></span>

<span data-ttu-id="5d267-152">Informacje dodatkowe: [CA2229: Zaimplementuj konstruktory serializacji](/visualstudio/code-quality/ca2229-implement-serialization-constructors)</span><span class="sxs-lookup"><span data-stu-id="5d267-152">Additional information: [CA2229: Implement serialization constructors](/visualstudio/code-quality/ca2229-implement-serialization-constructors)</span></span>

### <a name="ca2235-mark-all-non-serializable-fields"></a><span data-ttu-id="5d267-153">CA2235: Oznacz wszystkie pola nieprzeznaczone do serializacji</span><span class="sxs-lookup"><span data-stu-id="5d267-153">CA2235: Mark all non-serializable fields</span></span>

<span data-ttu-id="5d267-154">Pola wystąpienia typu, który nie może być serializowany, jest zadeklarowany w typie, który jest możliwy do serializacji.</span><span class="sxs-lookup"><span data-stu-id="5d267-154">An instance field of a type that is not serializable is declared in a type that is serializable.</span></span> <span data-ttu-id="5d267-155">Musisz wyraźnie oznaczyć tego pola z <xref:System.NonSerializedAttribute> naprawić to ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="5d267-155">You must explicitly mark that field with the <xref:System.NonSerializedAttribute> to fix this warning.</span></span>

<span data-ttu-id="5d267-156">**Kategoria:** Użycie</span><span class="sxs-lookup"><span data-stu-id="5d267-156">**Category:** Usage</span></span>

<span data-ttu-id="5d267-157">**Ważność:** Ostrzeżenie</span><span class="sxs-lookup"><span data-stu-id="5d267-157">**Severity:** Warning</span></span>

<span data-ttu-id="5d267-158">Informacje dodatkowe: [CA2235: Oznacz wszystkie pola nieprzeznaczone do](/visualstudio/code-quality/ca2235-mark-all-non-serializable-fields)</span><span class="sxs-lookup"><span data-stu-id="5d267-158">Additional information: [CA2235: Mark all non-serializable fields](/visualstudio/code-quality/ca2235-mark-all-non-serializable-fields)</span></span>

### <a name="ca2237-mark-iserializable-types-with-serializable"></a><span data-ttu-id="5d267-159">CA2237: Oznacz typy ISerializable atrybutem możliwy do serializacji</span><span class="sxs-lookup"><span data-stu-id="5d267-159">CA2237: Mark ISerializable types with serializable</span></span>

<span data-ttu-id="5d267-160">Aby zostały rozpoznane przez środowisko uruchomieniowe języka wspólnego jako możliwe do serializacji, typy muszą być oznaczone za pomocą <xref:System.SerializableAttribute> atrybutu nawet wtedy, gdy typ używa niestandardowych procedur serializacji przez zaimplementowanie <xref:System.Runtime.Serialization.ISerializable> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="5d267-160">To be recognized by the common language runtime as serializable, types must be marked by using the <xref:System.SerializableAttribute> attribute even when the type uses a custom serialization routine by implementing the <xref:System.Runtime.Serialization.ISerializable> interface.</span></span>

<span data-ttu-id="5d267-161">**Kategoria:** Użycie</span><span class="sxs-lookup"><span data-stu-id="5d267-161">**Category:** Usage</span></span>

<span data-ttu-id="5d267-162">**Ważność:** Ostrzeżenie</span><span class="sxs-lookup"><span data-stu-id="5d267-162">**Severity:** Warning</span></span>

<span data-ttu-id="5d267-163">Informacje dodatkowe: [CA2237: Oznacz typy ISerializable atrybutem możliwy do serializacji](/visualstudio/code-quality/ca2237-mark-iserializable-types-with-serializableattribute)</span><span class="sxs-lookup"><span data-stu-id="5d267-163">Additional information: [CA2237: Mark ISerializable types with serializable](/visualstudio/code-quality/ca2237-mark-iserializable-types-with-serializableattribute)</span></span>

### <a name="ca3075-insecure-dtd-processing-in-xml"></a><span data-ttu-id="5d267-164">CA3075: DTD niezabezpieczone przetwarzanie w formacie XML</span><span class="sxs-lookup"><span data-stu-id="5d267-164">CA3075: Insecure DTD processing in XML</span></span>

<span data-ttu-id="5d267-165">Jeśli używasz niezabezpieczone <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A> wystąpień lub odwołanie do jednostki zewnętrznej źródeł, analizator może akceptować niezaufanych danych wejściowych i ujawnienia poufnych informacji dla osób atakujących.</span><span class="sxs-lookup"><span data-stu-id="5d267-165">If you use insecure <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A> instances or reference external entity sources, the parser may accept untrusted input and disclose sensitive information to attackers.</span></span>  

<span data-ttu-id="5d267-166">**Kategoria:** Zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="5d267-166">**Category:** Security</span></span>

<span data-ttu-id="5d267-167">**Ważność:** Ostrzeżenie</span><span class="sxs-lookup"><span data-stu-id="5d267-167">**Severity:** Warning</span></span>

<span data-ttu-id="5d267-168">Informacje dodatkowe: [A3075: DTD niezabezpieczone przetwarzanie w formacie XML](/visualstudio/code-quality/ca2237-mark-iserializable-types-with-serializableattribute)</span><span class="sxs-lookup"><span data-stu-id="5d267-168">Additional information: [A3075: Insecure DTD processing in XML](/visualstudio/code-quality/ca2237-mark-iserializable-types-with-serializableattribute)</span></span>

### <a name="ca5350-do-not-use-weak-cryptographic-algorithms"></a><span data-ttu-id="5d267-169">CA5350: Nie używaj słabych algorytmów kryptograficznych</span><span class="sxs-lookup"><span data-stu-id="5d267-169">CA5350: Do not use weak cryptographic algorithms</span></span>

<span data-ttu-id="5d267-170">Algorytmy kryptograficzne zmniejsza się wraz z upływem czasu, jak ataki stają się bardziej zaawansowane.</span><span class="sxs-lookup"><span data-stu-id="5d267-170">Cryptographic algorithms degrade over time as attacks become more advanced.</span></span> <span data-ttu-id="5d267-171">W zależności od typu i aplikacji to algorytmów kryptograficznych, dalsze degradacji jego sile szyfrowania może umożliwić atakującemu odczytywanie komunikatów z enciphered, manipulowanie enciphered wiadomości, forge podpisów cyfrowych, manipulowanie skrótu zawartości lub w przeciwnym razie naruszenia wszelkich cryptosystem, w oparciu o ten algorytm.</span><span class="sxs-lookup"><span data-stu-id="5d267-171">Depending on the type and application of this cryptographic algorithm, further degradation of its cryptographic strength may allow attackers to read enciphered messages, tamper with enciphered messages, forge digital signatures, tamper with hashed content, or otherwise compromise any cryptosystem based on this algorithm.</span></span> <span data-ttu-id="5d267-172">Dla celów szyfrowania, Użyj algorytmu szyfrowania AES (AES-256, AES-192 i AES-128 są dopuszczalne) z kluczem o długości, większa niż lub równy 128 bitów.</span><span class="sxs-lookup"><span data-stu-id="5d267-172">For encryption, use an AES algorithm (AES-256, AES-192 and AES-128 are acceptable) with a key length greater than or equal to 128 bits.</span></span> <span data-ttu-id="5d267-173">Do tworzenia skrótów, użyj funkcji skrótu z rodziny SHA-2, np. 512 SHA-2, SHA-2-384 lub 256 SHA-2.</span><span class="sxs-lookup"><span data-stu-id="5d267-173">For hashing, use a hashing function in the SHA-2 family, such as SHA-2 512, SHA-2 384, or SHA-2 256.</span></span>

<span data-ttu-id="5d267-174">**Kategoria:** Zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="5d267-174">**Category:** Security</span></span>

<span data-ttu-id="5d267-175">**Ważność:** Ostrzeżenie</span><span class="sxs-lookup"><span data-stu-id="5d267-175">**Severity:** Warning</span></span>

<span data-ttu-id="5d267-176">Informacje dodatkowe: [CA5350: Nie używaj słabych algorytmów kryptograficznych](/visualstudio/code-quality/ca5350-do-not-use-weak-cryptographic-algorithms)</span><span class="sxs-lookup"><span data-stu-id="5d267-176">Additional information: [CA5350: Do not use weak cryptographic algorithms](/visualstudio/code-quality/ca5350-do-not-use-weak-cryptographic-algorithms)</span></span>

### <a name="ca5351-do-not-use-broken-cryptographic-algorithms"></a><span data-ttu-id="5d267-177">CA5351: Nie używaj uszkodzonych algorytmów kryptograficznych</span><span class="sxs-lookup"><span data-stu-id="5d267-177">CA5351: Do not use broken cryptographic algorithms</span></span>

<span data-ttu-id="5d267-178">Istnieje atak, dzięki czemu można przerwać ten algorytm wykonalne.</span><span class="sxs-lookup"><span data-stu-id="5d267-178">An attack making it computationally feasible to break this algorithm exists.</span></span> <span data-ttu-id="5d267-179">Pozwala to osobom atakującym przerwanie gwarancje kryptograficzne, które zaprojektowano w celu zapewnienia.</span><span class="sxs-lookup"><span data-stu-id="5d267-179">This allows attackers to break the cryptographic guarantees it is designed to provide.</span></span> <span data-ttu-id="5d267-180">W zależności od typu i aplikacji to algorytmów kryptograficznych to umożliwić osobom atakującym odczytywanie komunikatów z enciphered, manipulowanie enciphered wiadomości, forge podpisów cyfrowych, manipulowanie skrótu zawartości lub w przeciwnym razie naruszenia wszelkich cryptosystem na podstawie na ten algorytm.</span><span class="sxs-lookup"><span data-stu-id="5d267-180">Depending on the type and application of this cryptographic algorithm, this may allow attackers to read enciphered messages, tamper with enciphered messages, forge digital signatures, tamper with hashed content, or otherwise compromise any cryptosystem based on this algorithm.</span></span> <span data-ttu-id="5d267-181">Dla celów szyfrowania, Użyj algorytmu szyfrowania AES (AES-256, AES-192 i AES-128 są dopuszczalne) z kluczem o długości, większa niż lub równy 128 bitów.</span><span class="sxs-lookup"><span data-stu-id="5d267-181">For encryption, use an AES algorithm (AES-256, AES-192 and AES-128 are acceptable) with a key length greater than or equal to 128 bits.</span></span> <span data-ttu-id="5d267-182">Do tworzenia skrótów, użyj funkcji skrótu z rodziny SHA-2, takie jak SHA512, SHA384 lub SHA256.</span><span class="sxs-lookup"><span data-stu-id="5d267-182">For hashing, use a hashing function in the SHA-2 family, such as SHA512, SHA384, or SHA256.</span></span> <span data-ttu-id="5d267-183">W przypadku podpisów cyfrowych za pomocą RSA z kluczem o długości, większa niż lub równa 2048 bitów lub ECDSA długość klucza jest większa niż lub równa 256 bitów.</span><span class="sxs-lookup"><span data-stu-id="5d267-183">For digital signatures, use RSA with a key length greater than or equal to 2048-bits, or ECDSA with a key length greater than or equal to 256 bits.</span></span>

<span data-ttu-id="5d267-184">**Kategoria:** Zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="5d267-184">**Category:** Security</span></span>

<span data-ttu-id="5d267-185">**Ważność:** Ostrzeżenie</span><span class="sxs-lookup"><span data-stu-id="5d267-185">**Severity:** Warning</span></span>

<span data-ttu-id="5d267-186">Aby uzyskać dodatkowe informacje: [CA5351: Nie używaj uszkodzonych algorytmów kryptograficznych](/visualstudio/code-quality/ca5351-do-not-use-broken-cryptographic-algorithms)</span><span class="sxs-lookup"><span data-stu-id="5d267-186">Additional Information: [CA5351: Do not use broken cryptographic algorithms](/visualstudio/code-quality/ca5351-do-not-use-broken-cryptographic-algorithms)</span></span>

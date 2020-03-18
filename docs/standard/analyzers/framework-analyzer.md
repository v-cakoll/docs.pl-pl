---
title: Analizatory .NET Framework — .NET
description: Dowiedz się, jak używać analizatorów .NET Framework w pakiecie analizatorów .NET Framework do znajdowania i eliminowania zagrożeń bezpieczeństwa
author: billwagner
ms.author: wiwagn
ms.date: 01/25/2018
ms.technology: dotnet-standard
ms.openlocfilehash: dd69671e709549fe0ad0f582e4d09b43f7321df2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "78156000"
---
# <a name="the-net-framework-analyzer"></a><span data-ttu-id="233e9-103">Analizator platformy .NET Framework</span><span class="sxs-lookup"><span data-stu-id="233e9-103">The .NET Framework Analyzer</span></span>

<span data-ttu-id="233e9-104">Za pomocą analizatora .NET Framework można znaleźć potencjalne problemy w kodzie aplikacji opartym na platformie .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="233e9-104">You can use the .NET Framework Analyzer to find potential issues in your .NET Framework-based application code.</span></span> <span data-ttu-id="233e9-105">Ten analizator znajduje potencjalne problemy i sugeruje poprawki do nich.</span><span class="sxs-lookup"><span data-stu-id="233e9-105">This analyzer finds potential issues and suggests fixes to them.</span></span>

<span data-ttu-id="233e9-106">Analizator działa interaktywnie w programie Visual Studio podczas pisania kodu lub jako część kompilacji ci.</span><span class="sxs-lookup"><span data-stu-id="233e9-106">The analyzer runs interactively in Visual Studio as you write your code or as part of a CI build.</span></span> <span data-ttu-id="233e9-107">Należy dodać analizator do projektu tak wcześnie, jak to możliwe w rozwoju.</span><span class="sxs-lookup"><span data-stu-id="233e9-107">You should add the analyzer to your project as early as possible in your development.</span></span> <span data-ttu-id="233e9-108">Im szybciej znajdziesz jakieś potencjalne problemy w kodzie, tym łatwiej je naprawić.</span><span class="sxs-lookup"><span data-stu-id="233e9-108">The sooner you find any potential issues in your code, the easier they are to fix.</span></span> <span data-ttu-id="233e9-109">Jednak można dodać go w dowolnym momencie w cyklu rozwoju.</span><span class="sxs-lookup"><span data-stu-id="233e9-109">However, you can add it at any time in the development cycle.</span></span> <span data-ttu-id="233e9-110">Znajduje żadnych problemów z istniejącym kodem i ostrzega o nowych problemów podczas dalszego opracowywania.</span><span class="sxs-lookup"><span data-stu-id="233e9-110">It finds any issues with the existing code and warns about new issues as you keep developing.</span></span>

## <a name="installing-and-configuring-the-net-framework-analyzer"></a><span data-ttu-id="233e9-111">Instalowanie i konfigurowanie analizatora programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="233e9-111">Installing and configuring the .NET Framework Analyzer</span></span>

<span data-ttu-id="233e9-112">Analizatory .NET Framework muszą być zainstalowane jako pakiet NuGet w każdym projekcie, w którym mają być uruchamiane.</span><span class="sxs-lookup"><span data-stu-id="233e9-112">The .NET Framework Analyzers must be installed as a NuGet package on every project where you want them to run.</span></span> <span data-ttu-id="233e9-113">Tylko jeden deweloper musi dodać je do projektu.</span><span class="sxs-lookup"><span data-stu-id="233e9-113">Only one developer needs to add them to the project.</span></span> <span data-ttu-id="233e9-114">Pakiet analizatora jest zależnością projektu i będzie uruchamiany na komputerze każdego dewelopera, gdy ma zaktualizowane rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="233e9-114">The analyzer package is a project dependency and will run on every developer's machine once it has the updated solution.</span></span>

<span data-ttu-id="233e9-115">Analizator platformy .NET Framework jest dostarczany w pakiecie [NuGet programu Microsoft.NetFramework.Analyzers.](https://www.nuget.org/packages/Microsoft.NetFramework.Analyzers/)</span><span class="sxs-lookup"><span data-stu-id="233e9-115">The .NET Framework Analyzer is delivered in the [Microsoft.NetFramework.Analyzers](https://www.nuget.org/packages/Microsoft.NetFramework.Analyzers/) NuGet package.</span></span> <span data-ttu-id="233e9-116">Ten pakiet zawiera tylko analizatory specyficzne dla .NET Framework, który zawiera analizatory zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="233e9-116">This package provides only the analyzers specific to the .NET Framework, which includes security analyzers.</span></span> <span data-ttu-id="233e9-117">W większości przypadków należy [microsoft.codeanalysis.fxcopanalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) nuget pakietu.</span><span class="sxs-lookup"><span data-stu-id="233e9-117">In most cases, you'll want the [Microsoft.CodeAnalysis.FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) NuGet package.</span></span>
<span data-ttu-id="233e9-118">Pakiet zbiorczy FxCopAnalyzers zawiera wszystkie analizatory framework zawarte w pakiecie Framework.Analyzers, a także następujące analizatory:</span><span class="sxs-lookup"><span data-stu-id="233e9-118">The FxCopAnalyzers aggregate package contains all the framework analyzers included in the Framework.Analyzers package as well as the following analyzers:</span></span>

- <span data-ttu-id="233e9-119">[Microsoft.CodeQuality.Analyzeers](https://www.nuget.org/packages/Microsoft.CodeQuality.Analyzers): Zawiera ogólne wskazówki i wskazówki dotyczące standardowych interfejsów API platformy .NET</span><span class="sxs-lookup"><span data-stu-id="233e9-119">[Microsoft.CodeQuality.Analyzers](https://www.nuget.org/packages/Microsoft.CodeQuality.Analyzers): Provides general guidance and guidance for .NET Standard APIs</span></span>
- <span data-ttu-id="233e9-120">[Microsoft.NetCore.Analyzeers](https://www.nuget.org/packages/Microsoft.NetCore.Analyzers): Udostępnia analizatory specyficzne dla interfejsów API .NET Core.</span><span class="sxs-lookup"><span data-stu-id="233e9-120">[Microsoft.NetCore.Analyzers](https://www.nuget.org/packages/Microsoft.NetCore.Analyzers): Provides analyzers specific to .NET Core APIs.</span></span>
- <span data-ttu-id="233e9-121">[Text.Analyzeers](https://www.nuget.org/packages/Text.Analyzers): Zawiera wskazówki dotyczące tekstu dołączonego jako kod, w tym komentarzy.</span><span class="sxs-lookup"><span data-stu-id="233e9-121">[Text.Analyzers](https://www.nuget.org/packages/Text.Analyzers): Provides guidance for text included as code, including comments.</span></span>

<span data-ttu-id="233e9-122">Aby go zainstalować, kliknij prawym przyciskiem myszy projekt i wybierz polecenie "Zarządzaj zależnościami".</span><span class="sxs-lookup"><span data-stu-id="233e9-122">To install it, right-click on the project, and select "Manage Dependencies".</span></span>
<span data-ttu-id="233e9-123">Z nuget explorer, wyszukaj "NetFramework Analyzer", lub jeśli wolisz, "Fx Cop Analyzer".</span><span class="sxs-lookup"><span data-stu-id="233e9-123">From the NuGet explorer, search for "NetFramework Analyzer", or if you prefer, "Fx Cop Analyzer".</span></span> <span data-ttu-id="233e9-124">Zainstaluj najnowszą stabilną wersję we wszystkich projektach w rozwiązaniu.</span><span class="sxs-lookup"><span data-stu-id="233e9-124">Install the latest stable version in all projects in your solution.</span></span>

## <a name="using-the-net-framework-analyzer"></a><span data-ttu-id="233e9-125">Korzystanie z analizatora programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="233e9-125">Using the .NET Framework Analyzer</span></span>

<span data-ttu-id="233e9-126">Po zainstalowaniu pakietu NuGet skompiluj rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="233e9-126">Once the NuGet package is installed, build your solution.</span></span> <span data-ttu-id="233e9-127">Analizator zgłosi wszelkie problemy, które lokalizuje w bazie kodu.</span><span class="sxs-lookup"><span data-stu-id="233e9-127">The analyzer will report any issues it locates in your codebase.</span></span> <span data-ttu-id="233e9-128">Problemy są zgłaszane jako ostrzeżenia w oknie Lista błędów programu Visual Studio, jak pokazano na poniższym obrazie:</span><span class="sxs-lookup"><span data-stu-id="233e9-128">The issues are reported as warnings in the Visual Studio Error List window, as shown in the following image:</span></span>

![problemy zgłaszane przez analizator ram](./media/framework-analyzers-2.png)

<span data-ttu-id="233e9-130">Podczas pisania kodu, zobaczysz squiggles pod wszelkie potencjalne problem w kodzie.</span><span class="sxs-lookup"><span data-stu-id="233e9-130">As you write code, you see squiggles underneath any potential issue in your code.</span></span>
<span data-ttu-id="233e9-131">Umieść wskaźnik myszy na dowolnym problemie, a zobaczysz szczegóły dotyczące problemu oraz sugestie dotyczące wszelkich możliwych poprawek, jak pokazano na poniższym obrazku:</span><span class="sxs-lookup"><span data-stu-id="233e9-131">Hover over any issue and you see details about the issue, and suggestions for any possible fix, as shown in the following image:</span></span>

![interaktywny raport o problemach wykrytych przez analizator ram](./media/framework-analyzers-1.png)

<span data-ttu-id="233e9-133">Analizatory zbadać kod w rozwiązaniu i zapewnić listę ostrzeżeń dla każdego z tych problemów:</span><span class="sxs-lookup"><span data-stu-id="233e9-133">The analyzers examine the code in your solution and provide you with a list of warnings for any of these issues:</span></span>

### <a name="ca1058-types-should-not-extend-certain-base-types"></a><span data-ttu-id="233e9-134">CA1058: Typy nie powinny rozszerzać pewnych typów bazowych</span><span class="sxs-lookup"><span data-stu-id="233e9-134">CA1058: Types should not extend certain base types</span></span>

<span data-ttu-id="233e9-135">Istnieje niewielka liczba typów w .NET Framework, które nie powinny pochodzić bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="233e9-135">There are a small number of types in the .NET Framework that you should not derived from directly.</span></span>

<span data-ttu-id="233e9-136">**Kategoria:** Projektowania</span><span class="sxs-lookup"><span data-stu-id="233e9-136">**Category:** Design</span></span>

<span data-ttu-id="233e9-137">**Ważność:** ostrzeżenie</span><span class="sxs-lookup"><span data-stu-id="233e9-137">**Severity:** Warning</span></span>

<span data-ttu-id="233e9-138">Dodatkowe informacje: [CA:1058: Typy nie powinny rozszerzać niektórych typów podstawowych](/visualstudio/code-quality/ca1058-types-should-not-extend-certain-base-types)</span><span class="sxs-lookup"><span data-stu-id="233e9-138">Additional information: [CA:1058: Types should not extend certain base types](/visualstudio/code-quality/ca1058-types-should-not-extend-certain-base-types)</span></span>

### <a name="ca2153-do-not-catch-corrupted-state-exceptions"></a><span data-ttu-id="233e9-139">CA2153: Nie wychwytuj wyjątków stanu uszkodzonego</span><span class="sxs-lookup"><span data-stu-id="233e9-139">CA2153: Do not catch corrupted state exceptions</span></span>

<span data-ttu-id="233e9-140">Przechwytywanie wyjątków stanu uszkodzonego może maskować błędy (takie jak naruszenia dostępu), co powoduje niespójny stan wykonania lub ułatwia niebezpieczeństwo naruszenia systemu.</span><span class="sxs-lookup"><span data-stu-id="233e9-140">Catching corrupted state exceptions could mask errors (such as access violations), resulting in an inconsistent state of execution or making it easier for attackers to compromise a system.</span></span> <span data-ttu-id="233e9-141">Zamiast tego złapać i obsługiwać bardziej szczegółowy zestaw typów wyjątków lub ponownie zgłosić wyjątek</span><span class="sxs-lookup"><span data-stu-id="233e9-141">Instead, catch and handle a more specific set of exception type(s) or re-throw the exception</span></span>

<span data-ttu-id="233e9-142">**Kategoria:** Zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="233e9-142">**Category:** Security</span></span>

<span data-ttu-id="233e9-143">**Ważność:** ostrzeżenie</span><span class="sxs-lookup"><span data-stu-id="233e9-143">**Severity:** Warning</span></span>

<span data-ttu-id="233e9-144">Dodatkowe informacje: [## CA2153: Nie wyłapuj wyjątków stanu uszkodzonego](/visualstudio/code-quality/ca2153-avoid-handling-corrupted-state-exceptions)</span><span class="sxs-lookup"><span data-stu-id="233e9-144">Additional information: [## CA2153: Do not catch corrupted state exceptions](/visualstudio/code-quality/ca2153-avoid-handling-corrupted-state-exceptions)</span></span>

### <a name="ca2229-implement-serialization-constructors"></a><span data-ttu-id="233e9-145">CA2229: Należy zaimplementować konstruktory serializacji</span><span class="sxs-lookup"><span data-stu-id="233e9-145">CA2229: Implement serialization constructors</span></span>

<span data-ttu-id="233e9-146">Analizator generuje to ostrzeżenie podczas tworzenia typu, <xref:System.Runtime.Serialization.ISerializable> który implementuje interfejs, ale nie definiuje wymagany konstruktor serializacji.</span><span class="sxs-lookup"><span data-stu-id="233e9-146">The analyzer generates this warning when you create a type that implements the <xref:System.Runtime.Serialization.ISerializable> interface but does not define the required serialization constructor.</span></span> <span data-ttu-id="233e9-147">Aby naprawić naruszenie tej zasady, należy zaimplementować konstruktora serializacji.</span><span class="sxs-lookup"><span data-stu-id="233e9-147">To fix a violation of this rule, implement the serialization constructor.</span></span> <span data-ttu-id="233e9-148">Dla zamkniętej klasy należy ustawić konstruktor prywatny; w przeciwnym razie powinien być chroniony.</span><span class="sxs-lookup"><span data-stu-id="233e9-148">For a sealed class, make the constructor private; otherwise, make it protected.</span></span> <span data-ttu-id="233e9-149">Konstruktor serializacji ma następujący podpis:</span><span class="sxs-lookup"><span data-stu-id="233e9-149">The serialization constructor has the following signature:</span></span>

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

<span data-ttu-id="233e9-150">**Kategoria:** Użycia</span><span class="sxs-lookup"><span data-stu-id="233e9-150">**Category:** Usage</span></span>

<span data-ttu-id="233e9-151">**Ważność:** ostrzeżenie</span><span class="sxs-lookup"><span data-stu-id="233e9-151">**Severity:** Warning</span></span>

<span data-ttu-id="233e9-152">Dodatkowe informacje: [CA2229: Implementowanie konstruktorów serializacji](/visualstudio/code-quality/ca2229-implement-serialization-constructors)</span><span class="sxs-lookup"><span data-stu-id="233e9-152">Additional information: [CA2229: Implement serialization constructors](/visualstudio/code-quality/ca2229-implement-serialization-constructors)</span></span>

### <a name="ca2235-mark-all-non-serializable-fields"></a><span data-ttu-id="233e9-153">CA2235: Należy oznaczyć wszystkie nieserializowane pola</span><span class="sxs-lookup"><span data-stu-id="233e9-153">CA2235: Mark all non-serializable fields</span></span>

<span data-ttu-id="233e9-154">Pola wystąpienia typu, który nie może być serializowany, jest zadeklarowany w typie, który jest możliwy do serializacji.</span><span class="sxs-lookup"><span data-stu-id="233e9-154">An instance field of a type that is not serializable is declared in a type that is serializable.</span></span> <span data-ttu-id="233e9-155">Należy jawnie oznaczyć <xref:System.NonSerializedAttribute> to pole, aby naprawić to ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="233e9-155">You must explicitly mark that field with the <xref:System.NonSerializedAttribute> to fix this warning.</span></span>

<span data-ttu-id="233e9-156">**Kategoria:** Użycia</span><span class="sxs-lookup"><span data-stu-id="233e9-156">**Category:** Usage</span></span>

<span data-ttu-id="233e9-157">**Ważność:** ostrzeżenie</span><span class="sxs-lookup"><span data-stu-id="233e9-157">**Severity:** Warning</span></span>

<span data-ttu-id="233e9-158">Dodatkowe informacje: [CA2235: Oznacz wszystkie pola niepodlegające serializacji](/visualstudio/code-quality/ca2235-mark-all-non-serializable-fields)</span><span class="sxs-lookup"><span data-stu-id="233e9-158">Additional information: [CA2235: Mark all non-serializable fields](/visualstudio/code-quality/ca2235-mark-all-non-serializable-fields)</span></span>

### <a name="ca2237-mark-iserializable-types-with-serializable"></a><span data-ttu-id="233e9-159">CA2237: Mark ISerializable typy z serializable</span><span class="sxs-lookup"><span data-stu-id="233e9-159">CA2237: Mark ISerializable types with serializable</span></span>

<span data-ttu-id="233e9-160">Aby być rozpoznawanym przez program runtime języka wspólnego jako <xref:System.SerializableAttribute> serializable, typy muszą być oznaczone <xref:System.Runtime.Serialization.ISerializable> przy użyciu atrybutu, nawet wtedy, gdy typ używa niestandardowej procedury serializacji przez implementowanie interfejsu.</span><span class="sxs-lookup"><span data-stu-id="233e9-160">To be recognized by the common language runtime as serializable, types must be marked by using the <xref:System.SerializableAttribute> attribute even when the type uses a custom serialization routine by implementing the <xref:System.Runtime.Serialization.ISerializable> interface.</span></span>

<span data-ttu-id="233e9-161">**Kategoria:** Użycia</span><span class="sxs-lookup"><span data-stu-id="233e9-161">**Category:** Usage</span></span>

<span data-ttu-id="233e9-162">**Ważność:** ostrzeżenie</span><span class="sxs-lookup"><span data-stu-id="233e9-162">**Severity:** Warning</span></span>

<span data-ttu-id="233e9-163">Dodatkowe informacje: [CA2237: Mark ISerializable typy z serializable](/visualstudio/code-quality/ca2237-mark-iserializable-types-with-serializableattribute)</span><span class="sxs-lookup"><span data-stu-id="233e9-163">Additional information: [CA2237: Mark ISerializable types with serializable](/visualstudio/code-quality/ca2237-mark-iserializable-types-with-serializableattribute)</span></span>

### <a name="ca3075-insecure-dtd-processing-in-xml"></a><span data-ttu-id="233e9-164">CA3075: Niezabezpieczone przetwarzanie DTD w xml</span><span class="sxs-lookup"><span data-stu-id="233e9-164">CA3075: Insecure DTD processing in XML</span></span>

<span data-ttu-id="233e9-165">Jeśli używasz niezabezpieczonych <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A> wystąpień lub odwołujesz się do zewnętrznych źródeł encji, analizator może akceptować niezaufane dane wejściowe i ujawniać poufne informacje osobom atakującym.</span><span class="sxs-lookup"><span data-stu-id="233e9-165">If you use insecure <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A> instances or reference external entity sources, the parser may accept untrusted input and disclose sensitive information to attackers.</span></span>  

<span data-ttu-id="233e9-166">**Kategoria:** Zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="233e9-166">**Category:** Security</span></span>

<span data-ttu-id="233e9-167">**Ważność:** ostrzeżenie</span><span class="sxs-lookup"><span data-stu-id="233e9-167">**Severity:** Warning</span></span>

<span data-ttu-id="233e9-168">Dodatkowe informacje: [A3075: Niezabezpieczone przetwarzanie DTD w xml](/visualstudio/code-quality/ca2237-mark-iserializable-types-with-serializableattribute)</span><span class="sxs-lookup"><span data-stu-id="233e9-168">Additional information: [A3075: Insecure DTD processing in XML](/visualstudio/code-quality/ca2237-mark-iserializable-types-with-serializableattribute)</span></span>

### <a name="ca5350-do-not-use-weak-cryptographic-algorithms"></a><span data-ttu-id="233e9-169">CA5350: Nie używaj słabych algorytmów kryptograficznych</span><span class="sxs-lookup"><span data-stu-id="233e9-169">CA5350: Do not use weak cryptographic algorithms</span></span>

<span data-ttu-id="233e9-170">Algorytmy kryptograficzne ulegają degradacji w miarę postępów ataków.</span><span class="sxs-lookup"><span data-stu-id="233e9-170">Cryptographic algorithms degrade over time as attacks become more advanced.</span></span> <span data-ttu-id="233e9-171">W zależności od typu i zastosowania tego algorytmu kryptograficznego dalsza degradacja jego siły kryptograficznej może umożliwić napastnikom odczytywanie zaszyfrowanych wiadomości, manipulowanie zaszyfrowanymi wiadomościami, fałszowanie podpisów cyfrowych, manipulowanie haszowanymi treściami lub w przeciwnym razie naruszyć wszelkie kryptosystem oparty na tym algorytmie.</span><span class="sxs-lookup"><span data-stu-id="233e9-171">Depending on the type and application of this cryptographic algorithm, further degradation of its cryptographic strength may allow attackers to read enciphered messages, tamper with enciphered messages, forge digital signatures, tamper with hashed content, or otherwise compromise any cryptosystem based on this algorithm.</span></span> <span data-ttu-id="233e9-172">W przypadku szyfrowania należy użyć algorytmu AES (Dopuszczalne są AES-256, AES-192 i AES-128) o długości klucza większej lub równej 128 bitom.</span><span class="sxs-lookup"><span data-stu-id="233e9-172">For encryption, use an AES algorithm (AES-256, AES-192 and AES-128 are acceptable) with a key length greater than or equal to 128 bits.</span></span> <span data-ttu-id="233e9-173">W przypadku mieszania należy użyć funkcji mieszania w rodzinie SHA-2, takiej jak SHA-2 512, SHA-2 384 lub SHA-2 256.</span><span class="sxs-lookup"><span data-stu-id="233e9-173">For hashing, use a hashing function in the SHA-2 family, such as SHA-2 512, SHA-2 384, or SHA-2 256.</span></span>

<span data-ttu-id="233e9-174">**Kategoria:** Zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="233e9-174">**Category:** Security</span></span>

<span data-ttu-id="233e9-175">**Ważność:** ostrzeżenie</span><span class="sxs-lookup"><span data-stu-id="233e9-175">**Severity:** Warning</span></span>

<span data-ttu-id="233e9-176">Dodatkowe informacje: [CA5350: Nie używaj słabych algorytmów kryptograficznych](/visualstudio/code-quality/ca5350-do-not-use-weak-cryptographic-algorithms)</span><span class="sxs-lookup"><span data-stu-id="233e9-176">Additional information: [CA5350: Do not use weak cryptographic algorithms](/visualstudio/code-quality/ca5350-do-not-use-weak-cryptographic-algorithms)</span></span>

### <a name="ca5351-do-not-use-broken-cryptographic-algorithms"></a><span data-ttu-id="233e9-177">CA5351: Nie używaj uszkodzonych algorytmów kryptograficznych</span><span class="sxs-lookup"><span data-stu-id="233e9-177">CA5351: Do not use broken cryptographic algorithms</span></span>

<span data-ttu-id="233e9-178">Istnieje atak, dzięki czemu możliwe jest obliczenia, aby złamać ten algorytm.</span><span class="sxs-lookup"><span data-stu-id="233e9-178">An attack making it computationally feasible to break this algorithm exists.</span></span> <span data-ttu-id="233e9-179">Dzięki temu osoby atakujące mogą złamać gwarancje kryptograficzne, które ma zapewnić.</span><span class="sxs-lookup"><span data-stu-id="233e9-179">This allows attackers to break the cryptographic guarantees it is designed to provide.</span></span> <span data-ttu-id="233e9-180">W zależności od typu i zastosowania tego algorytmu kryptograficznego może to umożliwić osobom atakującym odczytywanie zaszyfrowanych wiadomości, manipulowanie zaszyfrowanymi wiadomościami, fałszowanie podpisów cyfrowych, manipulowanie haszowanymi treściami lub w inny sposób narażanie na szwank dowolnego opartego na systemie kryptograficznym na tym algorytmie.</span><span class="sxs-lookup"><span data-stu-id="233e9-180">Depending on the type and application of this cryptographic algorithm, this may allow attackers to read enciphered messages, tamper with enciphered messages, forge digital signatures, tamper with hashed content, or otherwise compromise any cryptosystem based on this algorithm.</span></span> <span data-ttu-id="233e9-181">W przypadku szyfrowania należy użyć algorytmu AES (Dopuszczalne są AES-256, AES-192 i AES-128) o długości klucza większej lub równej 128 bitom.</span><span class="sxs-lookup"><span data-stu-id="233e9-181">For encryption, use an AES algorithm (AES-256, AES-192 and AES-128 are acceptable) with a key length greater than or equal to 128 bits.</span></span> <span data-ttu-id="233e9-182">W przypadku mieszania należy użyć funkcji mieszania w rodzinie SHA-2, takiej jak SHA512, SHA384 lub SHA256.</span><span class="sxs-lookup"><span data-stu-id="233e9-182">For hashing, use a hashing function in the SHA-2 family, such as SHA512, SHA384, or SHA256.</span></span> <span data-ttu-id="233e9-183">W przypadku podpisów cyfrowych należy używać rsa o długości klucza większej lub równej 2048 bitom lub ECDSA o długości klucza większej lub równej 256 bitom.</span><span class="sxs-lookup"><span data-stu-id="233e9-183">For digital signatures, use RSA with a key length greater than or equal to 2048-bits, or ECDSA with a key length greater than or equal to 256 bits.</span></span>

<span data-ttu-id="233e9-184">**Kategoria:** Zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="233e9-184">**Category:** Security</span></span>

<span data-ttu-id="233e9-185">**Ważność:** ostrzeżenie</span><span class="sxs-lookup"><span data-stu-id="233e9-185">**Severity:** Warning</span></span>

<span data-ttu-id="233e9-186">Dodatkowe informacje: [CA5351: Nie używaj uszkodzonych algorytmów kryptograficznych](/visualstudio/code-quality/ca5351)</span><span class="sxs-lookup"><span data-stu-id="233e9-186">Additional Information: [CA5351: Do not use broken cryptographic algorithms](/visualstudio/code-quality/ca5351)</span></span>

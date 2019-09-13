---
title: Analizatory zabezpieczeń .NET — .NET
description: Dowiedz się, jak używać analizatorów zabezpieczeń .NET w pakiecie analizatorów .NET Framework, aby znajdować i rozwiązywać zagrożenia bezpieczeństwa
author: billwagner
ms.author: wiwagn
ms.date: 01/25/2018
ms.technology: dotnet-standard
ms.openlocfilehash: da5e72b96fec35404e7e9ae7930f3430143487d2
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70929310"
---
# <a name="the-net-framework-analyzer"></a>Analizator .NET Framework

Możesz użyć analizatora .NET Framework, aby znaleźć potencjalne problemy w kodzie aplikacji opartym na .NET Framework. Ten Analizator odnajdzie potencjalne problemy i sugeruje do nich poprawki.

Analizator działa interaktywnie w programie Visual Studio podczas pisania kodu lub jako część kompilacji elementu konfiguracji. Należy dodać Analizator do projektu tak szybko, jak to możliwe w rozwoju. Wkrótce znajdziesz ewentualne potencjalne problemy w kodzie, tym łatwiejsze jest ich naprawa. Można jednak dodać go w dowolnym momencie w cyklu projektowania. Znajduje wszelkie problemy związane z istniejącym kodem i ostrzega o nowych problemach związanych z programowaniem.

## <a name="installing-and-configuring-the-net-framework-analyzer"></a>Instalowanie i Konfigurowanie analizatora .NET Framework

Analizatory zabezpieczeń .NET muszą być zainstalowane jako pakiet NuGet w każdym projekcie, w którym mają być uruchamiane. Tylko jeden Deweloper musi dodać je do projektu. Pakiet analizatora jest zależnością projektu i będzie działać na każdym komputerze dewelopera, gdy ma zaktualizowane rozwiązanie.

Analizator .NET Framework jest dostarczany w pakiecie NuGet [Microsoft. NETFramework. analizators](https://www.nuget.org/packages/Microsoft.NetFramework.Analyzers/) . Ten pakiet zawiera tylko analizatory charakterystyczne dla .NET Framework, które obejmują analizatory zabezpieczeń. W większości przypadków należy użyć pakietu NuGet [Microsoft. CodeAnalysis. FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) . Pakiet zagregowany FxCopAnalyzers zawiera wszystkie analizatory struktury zawarte w pakiecie Framework. analizatory, a także następujące analizatory:

- [Microsoft. CodeQuality. analizatory](https://www.nuget.org/packages/Microsoft.CodeQuality.Analyzers): Zawiera ogólne wskazówki i wskazówki dotyczące .NET Standard interfejsów API
- [Microsoft. rdzeń. analizatory](https://www.nuget.org/packages/Microsoft.NetCore.Analyzers): Udostępnia analizatory charakterystyczne dla interfejsów API platformy .NET Core.
- [Text. analizatory](https://www.nuget.org/packages/Text.Analyzers): Zawiera wskazówki dotyczące tekstu zawartego w kodzie, w tym komentarzy.

Aby go zainstalować, kliknij prawym przyciskiem myszy projekt i wybierz polecenie "Zarządzaj zależnościami".
W Eksploratorze NuGet Wyszukaj ciąg "NetFramework Analyzer" lub, jeśli wolisz, "FX COP Analyzer". Zainstaluj najnowszą stabilną wersję we wszystkich projektach w rozwiązaniu.

## <a name="using-the-net-framework-analyzer"></a>Korzystanie z analizatora .NET Framework

Po zainstalowaniu pakietu NuGet Skompiluj rozwiązanie. Analizator zgłosi wszelkie problemy, które znajdują się w bazie kodu. Problemy są raportowane jako ostrzeżenia w oknie Lista błędów programu Visual Studio, jak pokazano na poniższej ilustracji:

![problemy zgłoszone przez analizator Framework](./media/framework-analyzers-2.png)

Podczas pisania kodu zobaczysz zygzaki poniżej dowolnego potencjalnego problemu w kodzie.
Umieść wskaźnik myszy nad dowolnym problemem i Wyświetl szczegóły dotyczące problemu oraz sugestie dotyczące ewentualnych poprawek, jak pokazano na poniższej ilustracji:

![interaktywny raport o problemach znalezionych przez analizator Framework](./media/framework-analyzers-1.png)

Analizatory sprawdzają kod w rozwiązaniu i zapewniają listę ostrzeżeń dla dowolnego z następujących problemów:

### <a name="ca1058-types-should-not-extend-certain-base-types"></a>CA1058: Typy nie powinny rozszerzać niektórych typów podstawowych

Istnieje niewielka liczba typów w .NET Framework, które nie powinny być bezpośrednio wyprowadzane. 

**Kategorii** Projekt

**Obrażeń** Ostrzeżenie

Informacje dodatkowe: [URZĄD CERTYFIKACJI: 1058: Typy nie powinny poszerzać niektórych typów podstawowych](/visualstudio/code-quality/ca1058-types-should-not-extend-certain-base-types)

### <a name="ca2153-do-not-catch-corrupted-state-exceptions"></a>CA2153: Nie Przechwytuj wyjątków uszkodzonych Stanów

Przechwycenie wyjątków uszkodzonego stanu może maskować błędy (takie jak naruszenia zasad dostępu), co spowodowało niespójny stan wykonywania lub ułatwianie atakującemu naruszenia bezpieczeństwa systemu. Zamiast tego należy przechwycić i obsłużyć bardziej szczegółowy zestaw typów wyjątków lub ponownie zgłosić wyjątek

**Kategorii** Zabezpieczenia

**Obrażeń** Ostrzeżenie

Informacje dodatkowe: [# # CA2153: Nie Przechwytuj wyjątków uszkodzonych Stanów](/visualstudio/code-quality/ca2153-avoid-handling-corrupted-state-exceptions)

### <a name="ca2229-implement-serialization-constructors"></a>CA2229: Zaimplementuj konstruktory serializacji

Analizator generuje to ostrzeżenie podczas tworzenia typu, który implementuje <xref:System.Runtime.Serialization.ISerializable> interfejs, ale nie definiuje wymaganego konstruktora serializacji. Aby naprawić naruszenie tej zasady, należy zaimplementować konstruktora serializacji. Dla zamkniętej klasy należy ustawić konstruktor prywatny; w przeciwnym razie powinien być chroniony. Konstruktor serializacji ma następujący podpis:

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

**Kategorii** Użycie

**Obrażeń** Ostrzeżenie

Informacje dodatkowe: [CA2229: Implementuj konstruktory serializacji](/visualstudio/code-quality/ca2229-implement-serialization-constructors)

### <a name="ca2235-mark-all-non-serializable-fields"></a>CA2235: Oznacz wszystkie pola nieprzeznaczone do serializacji

Pola wystąpienia typu, który nie może być serializowany, jest zadeklarowany w typie, który jest możliwy do serializacji. Należy jawnie oznaczyć to pole <xref:System.NonSerializedAttribute> , aby usunąć to ostrzeżenie.

**Kategorii** Użycie

**Obrażeń** Ostrzeżenie

Informacje dodatkowe: [CA2235 Oznacz wszystkie pola, które nie są możliwe do serializacji](/visualstudio/code-quality/ca2235-mark-all-non-serializable-fields)

### <a name="ca2237-mark-iserializable-types-with-serializable"></a>CA2237: Oznacz typy ISerializable z możliwością serializacji

Aby można było rozpoznać przez środowisko uruchomieniowe języka wspólnego jako możliwy do serializacji, typy muszą być <xref:System.SerializableAttribute> oznaczone przy użyciu atrybutu, nawet jeśli typ używa niestandardowej procedury serializacji przez <xref:System.Runtime.Serialization.ISerializable> implementację interfejsu.

**Kategorii** Użycie

**Obrażeń** Ostrzeżenie

Informacje dodatkowe: [CA2237 Oznacz typy ISerializable z możliwością serializacji](/visualstudio/code-quality/ca2237-mark-iserializable-types-with-serializableattribute)

### <a name="ca3075-insecure-dtd-processing-in-xml"></a>CA3075: Niezabezpieczone przetwarzanie DTD w kodzie XML

W przypadku korzystania z niezabezpieczonych <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A> wystąpień lub odwoływania się do zewnętrznych źródeł jednostek Analizator może zaakceptować niezaufane dane wejściowe i ujawnić poufne informacje osobom atakującym.  

**Kategorii** Zabezpieczenia

**Obrażeń** Ostrzeżenie

Informacje dodatkowe: [A3075: Niezabezpieczone przetwarzanie DTD w kodzie XML](/visualstudio/code-quality/ca2237-mark-iserializable-types-with-serializableattribute)

### <a name="ca5350-do-not-use-weak-cryptographic-algorithms"></a>CA5350: Nie używaj słabych algorytmów kryptograficznych

Algorytmy kryptograficzne obniżają wydajność w miarę upływu czasu, ponieważ ataki stają się bardziej zaawansowane. W zależności od typu i zastosowania tego algorytmu kryptograficznego, dalsze obniżenie jego siły kryptograficznej może pozwolić atakującemu na odczytywanie komunikatów ENCIPHERED, manipulowanie komunikatami ENCIPHERED, fałszowanie podpisów cyfrowych, manipulowanie skrótem zawartości lub w przeciwnym razie naruszyć wszelkie cryptosystem na podstawie tego algorytmu. W przypadku szyfrowania należy użyć algorytmu AES (AES-256, AES-192 i AES-128) o długości klucza większej lub równej 128 bitów. W celu utworzenia skrótu należy użyć funkcji mieszania w rodzinie SHA-2, takiej jak SHA-2 512, SHA-2 384 lub SHA-2 256.

**Kategorii** Zabezpieczenia

**Obrażeń** Ostrzeżenie

Informacje dodatkowe: [CA5350: Nie używaj słabych algorytmów kryptograficznych](/visualstudio/code-quality/ca5350-do-not-use-weak-cryptographic-algorithms)

### <a name="ca5351-do-not-use-broken-cryptographic-algorithms"></a>CA5351: Nie używaj uszkodzonych algorytmów kryptograficznych

Atak polegający na tym, że istnieje możliwość obliczeniowa tego algorytmu. Dzięki temu osoby atakujące mogą zerwać gwarancje kryptograficzne, które są przeznaczone do zapewnienia. W zależności od typu i zastosowania tego algorytmu kryptograficznego może to umożliwić osobom atakującym odczytywanie komunikatów ENCIPHERED, manipulowanie komunikatami ENCIPHERED, fałszowanie podpisów cyfrowych, manipulowanie skrótem zawartości lub w inny sposób naruszenie jakichkolwiek cryptosystem na podstawie dla tego algorytmu. W przypadku szyfrowania należy użyć algorytmu AES (AES-256, AES-192 i AES-128) o długości klucza większej lub równej 128 bitów. W celu utworzenia skrótów Użyj funkcji tworzenia skrótów w rodzinie SHA-2, takiej jak SHA512, SHA384 lub SHA256. W przypadku podpisów cyfrowych należy użyć klucza RSA o długości większej lub równej 2048-bitowej lub ECDSA z długością klucza większą lub równą 256 bitów.

**Kategorii** Zabezpieczenia

**Obrażeń** Ostrzeżenie

Informacje dodatkowe: [CA5351: Nie używaj uszkodzonych algorytmów kryptograficznych](/visualstudio/code-quality/ca5351-do-not-use-broken-cryptographic-algorithms)

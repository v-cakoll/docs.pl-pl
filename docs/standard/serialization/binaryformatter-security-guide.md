---
title: Przewodnik po zabezpieczeniach BinaryFormatter
description: W tym artykule opisano zagrożenia bezpieczeństwa związane z typem BinaryFormatter i zalecenia dla różnych serializatorów do użycia.
ms.date: 07/11/2020
ms.author: levib
author: GrabYourPitchforks
ms.openlocfilehash: f6a54b34bbf1e19212fe37aadb448a1722fe9ff0
ms.sourcegitcommit: 2543a78be6e246aa010a01decf58889de53d1636
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/17/2020
ms.locfileid: "86444767"
---
# <a name="binaryformatter-security-guide"></a>Przewodnik po zabezpieczeniach BinaryFormatter

Ten artykuł ma zastosowanie do następujących implementacji platformy .NET:

* .NET Framework wszystkie wersje
* .NET Core 2,1 — 3,1
* .NET 5,0 i nowsze

## <a name="background"></a>Tło

> [!WARNING]
> <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>Typ jest niebezpieczny i ***nie*** jest zalecany do przetwarzania danych. Aplikacje powinny przestać korzystać z programu `BinaryFormatter` tak szybko, jak to możliwe, nawet jeśli uważają, że dane są przez nie przetwarzane. `BinaryFormatter`nie może być zabezpieczony.

Ten artykuł dotyczy również następujących typów:

* <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>
* <xref:System.Runtime.Serialization.NetDataContractSerializer>
* <xref:System.Web.UI.LosFormatter>
* <xref:System.Web.UI.ObjectStateFormatter>

Luki deserializacji stanowią kategorię zagrożeń, w której ładunki żądań są niezabezpieczone. Osoba atakująca, która pomyślnie wykorzystuje te luki w zabezpieczeniach, może spowodować odmowę usługi (DoS), ujawnienie informacji lub zdalne wykonanie kodu w aplikacji docelowej. Ta kategoria ryzyka spójnie [OWASP 10](https://owasp.org/www-project-top-ten/). Elementy docelowe obejmują aplikacje w [różnych językach](https://owasp.org/www-community/vulnerabilities/Deserialization_of_untrusted_data), w tym C/C++, Java i C#.

W programie .NET największy cel ryzyka to aplikacje, które używają <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> typu do deserializacji danych. `BinaryFormatter`jest szeroko wykorzystywana w całym ekosystemie .NET ze względu na jego moc i łatwość użycia. Jednak ta sama moc zapewnia atakującemu możliwość wpływu na przepływ sterowania w aplikacji docelowej. Pomyślne ataki mogą spowodować, że osoba atakująca będzie mogła uruchomić kod w kontekście procesu docelowego.

W miarę uproszczenia należy założyć, że wywołanie `BinaryFormatter.Deserialize` przez ładunek jest odpowiednikiem interpretacji tego ładunku jako autonomicznego pliku wykonywalnego i uruchomienia go.

## <a name="binaryformatter-security-vulnerabilities"></a>BinaryFormatter luki w zabezpieczeniach

> [!WARNING]
> `BinaryFormatter.Deserialize`Metoda __nigdy nie__ jest bezpieczna, gdy jest używana z niezaufanymi danymi wejściowymi. Zdecydowanie zalecamy, aby zamiast tego rozważyć użycie jednego z alternatyw opisanych w dalszej części tego artykułu.

`BinaryFormatter`został zaimplementowany przed deserializacji luk w zabezpieczeniach była dobrze zrozumiałą kategorią zagrożeń. W związku z tym kod nie jest zgodny z nowoczesnymi najlepszymi rozwiązaniami. `Deserialize`Metoda może być używana jako wektor, aby osoby atakujące wykonywały ataki w systemie DOS przy użyciu aplikacji. Ataki te mogą spowodować, że aplikacja nie odpowiada lub spowodować zakończenie nieoczekiwanego procesu. Tej kategorii ataku nie można złagodzić przy użyciu `SerializationBinder` ani żadnego innego `BinaryFormatter` przełącznika konfiguracji. Platforma .NET uważa, że to zachowanie jest ***zaprojektowane*** i nie wystawia aktualizacji kodu w celu zmodyfikowania zachowania.

`BinaryFormatter.Deserialize`może być narażony na inne kategorie ataków, takie jak ujawnienie informacji lub zdalne wykonywanie kodu. Korzystanie z funkcji, takich jak niestandardowa, <xref:System.Runtime.Serialization.SerializationBinder> może być niewystarczające do prawidłowego ograniczenia tych zagrożeń. Istnieje możliwość, że zostanie wykryta Nowa Luka w zabezpieczeniach, dla której platforma .NET nie może praktycznie opublikować aktualizacji zabezpieczeń. Konsumenci powinni ocenić swoje poszczególne scenariusze i rozważyć ich potencjalną ekspozycję na te zagrożenia.

Zalecamy, aby `BinaryFormatter` klienci wykonywały indywidualne oceny ryzyka w aplikacjach. Jedyną odpowiedzialnością dla użytkownika jest określenie, czy należy korzystać z programu `BinaryFormatter` . Konsumenci powinni ocenić wymagania dotyczące bezpieczeństwa, technicznego, reputacji, prawne i przepisów prawnych dotyczących używania programu `BinaryFormatter` .

## <a name="preferred-alternatives"></a>Preferowane alternatywy

Platforma .NET oferuje kilka serializatorów wbudowanych, które mogą bezpiecznie obsłużyć dane niezaufane:

* <xref:System.Xml.Serialization.XmlSerializer>i <xref:System.Runtime.Serialization.DataContractSerializer> do serializacji grafów obiektów do i z XML. Nie należy mylić `DataContractSerializer` z <xref:System.Runtime.Serialization.NetDataContractSerializer> .
* <xref:System.IO.BinaryReader>oraz <xref:System.IO.BinaryWriter> dla plików XML i JSON.
* <xref:System.Text.Json>Interfejsy API do serializacji grafów obiektów do formatu JSON.

## <a name="dangerous-alternatives"></a>Niebezpieczne alternatywy

Unikaj następujących serializacji:

* <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>
* <xref:System.Web.UI.LosFormatter>
* <xref:System.Runtime.Serialization.NetDataContractSerializer>
* <xref:System.Web.UI.ObjectStateFormatter>

Poprzednie serializatory wykonują nieograniczone deserializacji polimorficzne i są niebezpieczne, podobnie jak `BinaryFormatter` .

## <a name="the-risks-of-assuming-data-to-be-trustworthy"></a>Ryzyko związane z założeniem, że dane są wiarygodne

Często Deweloper aplikacji może uznać, że przetwarza tylko zaufane dane wejściowe. Bezpieczny przypadek wejściowy ma wartość true w niektórych rzadkich przypadkach. Jednak jest to znacznie bardziej powszechne, że ładunek przecina granicę zaufania bez dewelopera.

__Rozważmy serwer Premium, w__ którym pracownicy korzystają z klienta stacjonarnego ze swoich stacji roboczych, aby móc korzystać z usługi. Ten scenariusz może być widziany naïvely jako "bezpieczna" Konfiguracja, w której wykorzystanie `BinaryFormatter` jest akceptowalne. Jednak ten scenariusz przedstawia wektor dla złośliwego oprogramowania, które uzyskuje dostęp do maszyny jednego pracownika, aby można było rozmieścić w całym przedsiębiorstwie. Złośliwe oprogramowanie może wykorzystać w `BinaryFormatter` celu późniejszego przechodzenia od stacji roboczej pracownika do serwera wewnętrznej bazy danych. Następnie może wyprowadzać dane poufne firmy. Takie dane mogą obejmować tajemnice handlowe lub dane klientów.

__Rozważ również aplikację, która używa `BinaryFormatter` do utrwalania stanu zapisywania.__ Może to być na początku bezpieczny scenariusz, ponieważ odczytywanie i zapisywanie danych na własnym dysku twardym reprezentuje drobne zagrożenie. Jednak udostępnianie dokumentów za pośrednictwem poczty e-mail lub Internetu jest wspólne, a większość użytkowników końcowych nie odczuwa otwierania tych pobranych plików jako ryzykownych zachowań.

Ten scenariusz może być używany do szkodliwa efektu. Jeśli aplikacja jest grą, użytkownicy, którzy udostępniają pliki z zapisywaniem, nie są świadomie zagrożeni. Deweloperzy mogą również być dołączani. Osoba atakująca może wysłać wiadomość e-mail do pomocy technicznej dla deweloperów, dołączyć złośliwy plik danych i zadawać personelowi pomocy technicznej jego otwarcie. Ataki tego rodzaju mogą dać atakującemu przyczółka w przedsiębiorstwie.

Inny scenariusz polega na tym, że plik danych jest przechowywany w magazynie w chmurze i automatycznie synchronizowany między maszynami użytkownika. Osoba atakująca, która będzie mogła uzyskać dostęp do konta magazynu w chmurze, może zatruć plik danych. Ten plik danych zostanie automatycznie zsynchronizowany z maszynami użytkownika. Gdy następnym razem użytkownik otworzy plik danych, zostanie uruchomiony ładunek osoby atakującej. W ten sposób osoba atakująca może wykorzystać kompromisy dla konta magazynu w chmurze, aby uzyskać pełne uprawnienia do wykonywania kodu.

__Rozważmy aplikację przenoszącą się z modelu instalacji klasycznej do modelu w chmurze.__ Ten scenariusz obejmuje aplikacje, które przechodzą z aplikacji klasycznej lub bogatego modelu klienta do modelu opartego na sieci Web. Wszelkie modele zagrożeń narysowane dla aplikacji klasycznej nie są koniecznie stosowane do usługi w chmurze. Model zagrożeń dla aplikacji klasycznej może odrzucić określone zagrożenie jako "nieinteresujące dla klienta". Jednak to samo zagrożenie może być interesujące, gdy uzna, że użytkownik zdalny nie atakuje samej usługi w chmurze.

> [!NOTE]
> Ogólnie rzecz biorąc, zamiar serializacji polega na przesłaniu obiektu do lub z aplikacji. Korzystanie z modelowania zagrożeń prawie zawsze oznacza tego rodzaju transfer danych jako Przekroczenie granicy zaufania.

## <a name="further-resources"></a>Dalsze zasoby

* [YSoSerial.NET](https://github.com/pwntester/ysoserial.net) na to, w jaki sposób aplikacje atakujące źródłami ataków korzystają z programu `BinaryFormatter` .
* [Modelowanie zagrożeń](/securityengineering/sdl/threatmodeling) na potrzeby informacji dotyczących aplikacji i usług modelowania zagrożeń.
* Ogólne w przypadku luk deserializacji:
  * [OWASP 10-A8:2017 — niezabezpieczona deserializacja](https://owasp.org/www-project-top-ten/OWASP_Top_Ten_2017/Top_10-2017_A8-Insecure_Deserialization)
  * [CWE-502: deserializacja niezaufanych danych](https://cwe.mitre.org/data/definitions/502.html)

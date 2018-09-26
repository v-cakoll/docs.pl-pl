---
title: Obsługa identyfikatorów zasobów międzynarodowych w System.Uri
ms.date: 03/30/2017
ms.assetid: b5e994c3-3535-4aff-8e1b-b69be22e9a22
author: mcleblanc
ms.author: markl
ms.openlocfilehash: ef44453dce2f59a2b481d0533b8bd28de516c630
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47156569"
---
# <a name="international-resource-identifier-support-in-systemuri"></a>Obsługa identyfikatorów zasobów międzynarodowych w System.Uri
<xref:System.Uri?displayProperty=nameWithType> Klasa została rozszerzona z obsługą międzynarodowych nazw domen (IDN) i międzynarodowych identyfikatorów zasobów (IRI). Te rozszerzenia są dostępne w programie .NET Framework 3.5, 3.0 z dodatkiem SP1 i 2.0 z dodatkiem SP1.  
  
## <a name="iri-and-idn-support"></a>IRI i obsługi IDN  
 Adresy sieci Web zwykle są wyrażone za pomocą identyfikatorów URI (Uniform Resource) który składa się z bardzo ograniczony zestaw znaków:  
  
-   Wielkich i małych liter ASCII litery z alfabetu angielskiego.  
  
-   Cyfry od 0 do 9.  
  
-   Niewielka liczba innych symboli ASCII.  
  
 Specyfikacje dotyczące identyfikatorów URI są opisane w dokumencie RFC 2396 i opublikowane przez Internet Engineering Task Force (IETF) ze standardem RFC 3986.  
  
 Rozwój Internetu jest rosnąca potrzeba identyfikacji zasobów, w językach innych niż angielski. Identyfikatory, które ułatwiają te potrzeby i Zezwalaj na znaki spoza zestawu ASCII (liczba znaków w zestawie znaków Unicode/ISO 10646) są znane jako międzynarodowych identyfikatorach zasobów (IRIs). Specyfikacje dotyczące IRIs są opisane w specyfikacji RFC 3987 opublikowane przez grupę IETF. Za pomocą IRIs umożliwia adresu URL zawierała znaki Unicode.  
  
 Istniejące <xref:System.Uri?displayProperty=nameWithType> klasa została rozszerzona, aby zapewnić obsługę IRI oparte na specyfikacji RFC 3987. Bieżąca liczba użytkowników nie będą widzieć wszelkie zmiany w zachowaniu .NET Framework 2.0, chyba że jawnie włączyć IRI. Dzięki temu zgodność aplikacji z wcześniejszych wersji programu .NET Framework.  
  
 Aplikacja może określić, czy ma być używany, analizy Zinternacjonalizowanych nazw domen (IDN), stosowane do nazw domen, czy powinna być stosowana IRI podczas analizowania reguły. Można to zrobić w pliku machine.config lub w pliku app.config.  
  
 Włączanie IDN, spowoduje przekonwertowanie wszystkich etykiet Unicode w nazwie domeny na ich odpowiedniki Punycode. Nazwy Punycode zawierać tylko znaki ASCII i zawsze rozpoczynają się prefiksem xn —. Przyczyną tego jest do obsługi istniejących serwerów DNS w Internecie, ponieważ większość serwery DNS obsługują tylko znaki ASCII (zobacz RFC 3940).  
  
 Włączanie IRI i IDN ma wpływ na wartość <xref:System.Uri.DnsSafeHost%2A?displayProperty=nameWithType> właściwości. Włączanie IRI i IDN można również zmienić zachowanie <xref:System.Uri.Equals%2A?displayProperty=nameWithType>, <xref:System.Uri.OriginalString%2A?displayProperty=nameWithType>, <xref:System.Uri.GetComponents%2A?displayProperty=nameWithType>, i <xref:System.Uri.IsWellFormedOriginalString%2A> metody.  
  
 <xref:System.GenericUriParser?displayProperty=nameWithType> Klasy ma również rozszerzone możliwości tworzenia dostosowywalne analizatora składni, która obsługuje IRI i IDN. Zachowanie <xref:System.GenericUriParser?displayProperty=nameWithType> obiektu jest określony przez przekazanie bitowa kombinacja wartości, które są dostępne w <xref:System.GenericUriParserOptions?displayProperty=nameWithType> wyliczeniu, aby <xref:System.GenericUriParser?displayProperty=nameWithType> konstruktora. <xref:System.GenericUriParserOptions.IriParsing?displayProperty=nameWithType> Typ wskazuje parser obsługuje reguły analizy składni określony w RFC 3987 dla międzynarodowych identyfikatorów zasobów (IRI). Czy IRI będzie faktycznie używana jest zależna od czy IRI jest włączony.  
  
 <xref:System.GenericUriParserOptions.Idn?displayProperty=nameWithType> Typ wskazuje parser obsługuje międzynarodowych nazw domen (IDN) podczas analizowania (IDN) nazw hostów. Czy IDN będzie faktycznie używana jest zależna od czy IDN jest włączony.  
  
 Włączenie IRI analiza kodu będzie wykonywał normalizacji i znak sprawdzanie zgodnie z IRI najnowsze reguły w specyfikacji RFC 3987. Wartość domyślna to dla IRI analizowania wyłączona, dlatego normalizacji i sprawdzanie znaków, które są wykonywane zgodnie z RFC 2396 i ze standardem RFC 3986.  
  
 IRI i IDN, przetwarzanie w <xref:System.Uri?displayProperty=nameWithType> klasy można również sterować przy użyciu <xref:System.Configuration.IriParsingElement?displayProperty=nameWithType> i <xref:System.Configuration.IdnElement?displayProperty=nameWithType> klasy ustawień konfiguracji. <xref:System.Configuration.IriParsingElement?displayProperty=nameWithType> Ustawienie włącza lub wyłącza IRI przetwarzanie w <xref:System.Uri?displayProperty=nameWithType> klasy. <xref:System.Configuration.IdnElement?displayProperty=nameWithType> Ustawienie włącza lub wyłącza IDN, przetwarzanie w <xref:System.Uri> klasy. <xref:System.Configuration.IriParsingElement?displayProperty=nameWithType> Ustawienie pośrednio kontroluje IDN. Przetwarzanie IRI musi być włączona dla IDN, przetwarzania, aby zawsze jest możliwe. Jeśli przetwarzanie IRI jest wyłączone, ustawienie domyślne, których zachowanie środowiska .NET Framework 2.0 jest używany do zapewnienia zgodności i nazwy IDN nie są używane ustawiony jest IDN przetwarzania.  
  
 Ustawienie konfiguracji dotyczące <xref:System.Configuration.IriParsingElement?displayProperty=nameWithType> i <xref:System.Configuration.IdnElement?displayProperty=nameWithType> klas konfiguracji zostanie odczytany raz podczas pierwszej <xref:System.Uri?displayProperty=nameWithType> klasy. Zmiany ustawień konfiguracji po tym czasie są ignorowane.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Configuration.IdnElement?displayProperty=nameWithType>  
 <xref:System.Configuration.IriParsingElement?displayProperty=nameWithType>  
 <xref:System.Uri?displayProperty=nameWithType>  
 <xref:System.Uri.DnsSafeHost%2A?displayProperty=nameWithType>

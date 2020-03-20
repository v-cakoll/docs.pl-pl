---
title: Obsługa identyfikatorów zasobów międzynarodowych w System.Uri
ms.date: 03/30/2017
ms.assetid: b5e994c3-3535-4aff-8e1b-b69be22e9a22
ms.openlocfilehash: f78fff250aae177b5f0360e77a1c41a2f2bb0527
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "64647336"
---
# <a name="international-resource-identifier-support-in-systemuri"></a>Obsługa identyfikatorów zasobów międzynarodowych w System.Uri
Klasa <xref:System.Uri?displayProperty=nameWithType> została rozszerzona o obsługę międzynarodowych identyfikatorów zasobów (IRI) i internationalized Domain Names (IDN). Te ulepszenia są dostępne w .NET Framework 3.5, 3.0 SP1 i 2.0 SP1.  
  
## <a name="iri-and-idn-support"></a>Obsługa IRI i IDN  
 Adresy sieci Web są zazwyczaj wyrażane przy użyciu jednolitych identyfikatorów zasobów (URI), które składają się z bardzo ograniczonego zestawu znaków:  
  
- Wielkie i małe litery ASCII z alfabetu angielskiego.  
  
- Cyfry od 0 do 9.  
  
- Niewielka liczba innych symboli ASCII.  
  
 Specyfikacje URI są udokumentowane w RFC 2396 i RFC 3986 opublikowane przez Internet Engineering Task Force (IETF).  
  
 Wraz z rozwojem Internetu rośnie potrzeba identyfikacji zasobów przy użyciu języków innych niż angielski. Identyfikatory, które ułatwiają tę potrzebę i zezwalają na znaki inne niż ASCII (znaki w zestawie znaków Unicode/ISO 10646) są znane jako międzynarodowe identyfikatory zasobów (IRC). Specyfikacje iRC są udokumentowane w RFC 3987 opublikowanym przez IETF. Korzystanie z funkcji IRC umożliwia adres URL zawierający znaki Unicode.  
  
 Istniejąca <xref:System.Uri?displayProperty=nameWithType> klasa została rozszerzona, aby zapewnić obsługę IRI na podstawie RFC 3987. Obecni użytkownicy nie zobaczą żadnych zmian w zachowaniu programu .NET Framework 2.0, chyba że w szczególności włączą IRI. Zapewnia to zgodność aplikacji z wcześniejszymi wersjami programu .NET Framework.  
  
 Aplikacja może określić, czy do nazw domen ma być stosowana analizowanie internationalized Domain Name (IDN) i czy należy stosować reguły analizowania IRI. Można to zrobić w pliku machine.config lub w pliku app.config.  
  
 Włączenie nazwy IDN spowoduje przekonwertowanie wszystkich etykiet Unicode w nazwie domeny na ich odpowiedniki Punycode. Nazwy punycode zawierają tylko znaki ASCII i zawsze zaczynają się od prefiksu xn-- Powodem tego jest obsługa istniejących serwerów DNS w Internecie, ponieważ większość serwerów DNS obsługuje tylko znaki ASCII (patrz RFC 3940).  
  
 Włączenie IRI i IDN wpływa na <xref:System.Uri.DnsSafeHost%2A?displayProperty=nameWithType> wartość właściwości. Włączenie IRI i IDN może również <xref:System.Uri.Equals%2A?displayProperty=nameWithType>zmienić <xref:System.Uri.GetComponents%2A?displayProperty=nameWithType>zachowanie <xref:System.Uri.IsWellFormedOriginalString%2A> , <xref:System.Uri.OriginalString%2A?displayProperty=nameWithType>, i metody.  
  
 Klasa <xref:System.GenericUriParser?displayProperty=nameWithType> została również rozszerzona, aby umożliwić tworzenie konfigurowalny parser, który obsługuje IRI i IDN. Zachowanie <xref:System.GenericUriParser?displayProperty=nameWithType> obiektu jest określony przez przekazywanie bitowej kombinacji wartości <xref:System.GenericUriParserOptions?displayProperty=nameWithType> dostępnych w wyliczeniu do konstruktora. <xref:System.GenericUriParser?displayProperty=nameWithType> Typ <xref:System.GenericUriParserOptions.IriParsing?displayProperty=nameWithType> wskazuje, że analizator obsługuje reguły analizowania określone w RFC 3987 dla międzynarodowych identyfikatorów zasobów (IRI). To, czy IRI jest rzeczywiście używane, zależy od tego, czy IRI jest włączone.  
  
 Typ <xref:System.GenericUriParserOptions.Idn?displayProperty=nameWithType> wskazuje, że analizator obsługuje analizowanie internationalized Domain Name (IDN) nazw hostów.The type indicates the parser supports Internationalized Domain Name (IDN) parsing (IDN) of host names. To, czy IDN jest faktycznie używane, zależy od tego, czy jest włączona funkcja IDN.  
  
 Włączenie analizy IRI spowoduje normalizację i sprawdzanie znaków zgodnie z najnowszymi regułami IRI w RFC 3987. Wartość domyślna jest dla analizy IRI, aby wyłączyć, więc normalizacji i sprawdzania znaków są wykonywane zgodnie z RFC 2396 i RFC 3986.  
  
 Przetwarzanie IRI i IDN w <xref:System.Uri?displayProperty=nameWithType> klasie można <xref:System.Configuration.IriParsingElement?displayProperty=nameWithType> <xref:System.Configuration.IdnElement?displayProperty=nameWithType> również kontrolować przy użyciu klas ustawień konfiguracji i. Ustawienie <xref:System.Configuration.IriParsingElement?displayProperty=nameWithType> włącza lub wyłącza przetwarzanie <xref:System.Uri?displayProperty=nameWithType> IRI w klasie. Ustawienie <xref:System.Configuration.IdnElement?displayProperty=nameWithType> włącza lub wyłącza przetwarzanie IDN w <xref:System.Uri> klasie. Ustawienie <xref:System.Configuration.IriParsingElement?displayProperty=nameWithType> również pośrednio kontroluje IDN. Przetwarzanie IRI musi być włączone, aby przetwarzanie IDN było możliwe. Jeśli przetwarzanie IRI jest wyłączone, przetwarzanie IDN zostanie ustawione na ustawienie domyślne, w którym zachowanie programu .NET Framework 2.0 jest używane do zgodności, a nazwy IDN nie są używane.  
  
 Ustawienie konfiguracji dla <xref:System.Configuration.IriParsingElement?displayProperty=nameWithType> <xref:System.Configuration.IdnElement?displayProperty=nameWithType> klas konfiguracji i zostaną odczytane raz podczas konstruowania pierwszej <xref:System.Uri?displayProperty=nameWithType> klasy. Zmiany ustawień konfiguracji po tym czasie są ignorowane.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Configuration.IdnElement?displayProperty=nameWithType>
- <xref:System.Configuration.IriParsingElement?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- <xref:System.Uri.DnsSafeHost%2A?displayProperty=nameWithType>

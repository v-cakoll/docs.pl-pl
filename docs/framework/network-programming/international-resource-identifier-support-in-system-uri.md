---
title: "Obsługa identyfikatora zasobu międzynarodowe w System.Uri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b5e994c3-3535-4aff-8e1b-b69be22e9a22
caps.latest.revision: "9"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 7946bdef8ebe93e9298850635ce46257533ab121
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="international-resource-identifier-support-in-systemuri"></a>Obsługa identyfikatora zasobu międzynarodowe w System.Uri
<xref:System.Uri?displayProperty=nameWithType> Klasy został rozszerzony międzynarodowej identyfikator zasobów (IRI) i obsługa międzynarodowych nazw domen (IDN). Rozszerzenia te są dostępne w .NET Framework 3.5, 3.0 z dodatkiem SP1, 2.0 z dodatkiem SP1.  
  
## <a name="iri-and-idn-support"></a>IRI i IDN pomocy technicznej  
 Adresy sieci Web są zazwyczaj podawana przy użyciu identyfikatorów URI (Uniform Resource) który składa się z bardzo ograniczony zestaw znaków:  
  
-   Wielkie i małe litery ASCII litery z alfabetu angielskiego.  
  
-   Cyfry z przedziału od 0 do 9.  
  
-   Mała liczba innych symboli ASCII.  
  
 Specyfikacje identyfikatory URI są opisane w dokumencie RFC 2396 i RFC 3986 opublikowane przez Internet Engineering Task Force (IETF).  
  
 Rozwój Internetu jest rośnie potrzeba zidentyfikuj zasoby przy użyciu języków innych niż angielski. Identyfikatory, które ułatwiają te wymagania i zezwalać na znaki spoza zestawu ASCII (znaki w zestawie znaków Unicode/ISO 10646) są nazywane międzynarodowej identyfikatory zasobów (IRIs). Specyfikacje tęczówki są udokumentowane w 3987 RFC opublikowanych przez grupę roboczą IETF. Przy użyciu IRIs umożliwia adres URL zawiera znaki Unicode.  
  
 Istniejące <xref:System.Uri?displayProperty=nameWithType> klasa została rozszerzona, aby zapewnić obsługę IRI oparte na RFC 3987. Bieżąca liczba użytkowników nie będą widzieć wszystkie zmiany z zachowaniem .NET Framework 2.0, chyba że jawnie włączyć IRI. Dzięki temu zgodność aplikacji we wcześniejszych wersjach programu .NET Framework.  
  
 Aplikację można określić, czy użyć międzynarodowych nazw domen (IDN) podczas analizowania stosowane do nazwy domeny i czy powinny być stosowane IRI podczas analizowania reguły. Można to zrobić w pliku machine.config lub w pliku app.config.  
  
 Włączanie IDN przekonwertuje wszystkich etykiet Unicode w domenie o nazwie odpowiedniki ciąg Punycode. Ciąg Punycode nazwy zawierają tylko znaki ASCII i zawsze rozpoczyna się od prefiksu xn--. Przyczyną tego jest do obsługi istniejących serwerów DNS w Internecie, ponieważ większość serwery DNS obsługują tylko znaki ASCII (zobacz dokument RFC 3940).  
  
 Włączenie IRI i IDN ma wpływ na wartość <xref:System.Uri.DnsSafeHost%2A?displayProperty=nameWithType> właściwości. Włączenie IRI i IDN można również zmienić zachowanie <xref:System.Uri.Equals%2A?displayProperty=nameWithType>, <xref:System.Uri.OriginalString%2A?displayProperty=nameWithType>, <xref:System.Uri.GetComponents%2A?displayProperty=nameWithType>, i <xref:System.Uri.IsWellFormedOriginalString%2A> metody.  
  
 <xref:System.GenericUriParser?displayProperty=nameWithType> Również został rozszerzony klasa umożliwia tworzenie można dostosowywać analizator obsługującego IRI i IDN. Zachowanie <xref:System.GenericUriParser?displayProperty=nameWithType> obiektu jest określona przez przekazanie bitowe połączenie wartości, które są dostępne w <xref:System.GenericUriParserOptions?displayProperty=nameWithType> wyliczeniu, aby <xref:System.GenericUriParser?displayProperty=nameWithType> konstruktora. <xref:System.GenericUriParserOptions.IriParsing?displayProperty=nameWithType> Typ wskazuje parser obsługuje podczas analizowania reguły, określona w dokumencie RFC 3987 dla identyfikatorów zasobów międzynarodowych (IRI). Określa, czy rzeczywiście służy IRI zależy od czy IRI jest włączone.  
  
 <xref:System.GenericUriParserOptions.Idn?displayProperty=nameWithType> Typ wskazuje parser obsługuje nazwę domeny (IDN) podczas analizowania (IDN) nazw hostów. Określa, czy rzeczywiście służy IDN zależy od Jeśli włączono IDN.  
  
 Włączenie IRI analizowania wykona normalizacji i znak sprawdzanie zgodnie z IRI najnowsze zasady w dokumencie RFC 3987. Wartość domyślna to dla IRI analizowania wyłączona, więc normalizacji i sprawdzanie znak są przeprowadzane zgodnie z RFC 2396 i RFC 3986.  
  
 IRI i IDN przetwarzania w <xref:System.Uri?displayProperty=nameWithType> klasy można także kontrolować przy użyciu <xref:System.Configuration.IriParsingElement?displayProperty=nameWithType> i <xref:System.Configuration.IdnElement?displayProperty=nameWithType> klasy ustawień konfiguracji. <xref:System.Configuration.IriParsingElement?displayProperty=nameWithType> Ustawienie włącza lub wyłącza IRI przetwarzania w <xref:System.Uri?displayProperty=nameWithType> klasy. <xref:System.Configuration.IdnElement?displayProperty=nameWithType> Ustawienie włącza lub wyłącza IDN przetwarzania w <xref:System.Uri> klasy. <xref:System.Configuration.IriParsingElement?displayProperty=nameWithType> Ustawienie również pośrednio steruje IDN. Przetwarzanie IRI musi być włączona dla przetwarzania w celu umożliwienia IDN. Po wyłączeniu przetwarzania IRI przetwarzania IDN zostanie ustawiona do ustawienie domyślne, których zachowanie programu .NET Framework 2.0 jest używany dla zgodności i nazwy IDN nie są używane.  
  
 Ustawienia konfiguracji dla <xref:System.Configuration.IriParsingElement?displayProperty=nameWithType> i <xref:System.Configuration.IdnElement?displayProperty=nameWithType> klas konfiguracji zostaną odczytane raz po pierwszym <xref:System.Uri?displayProperty=nameWithType> klasy jest tworzony. Zmiany ustawień konfiguracji po tym czasie są ignorowane.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Configuration.IdnElement?displayProperty=nameWithType>  
 <xref:System.Configuration.IriParsingElement?displayProperty=nameWithType>  
 <xref:System.Uri?displayProperty=nameWithType>  
 <xref:System.Uri.DnsSafeHost%2A?displayProperty=nameWithType>

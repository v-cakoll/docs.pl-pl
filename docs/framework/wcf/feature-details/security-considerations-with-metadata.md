---
title: Zagadnienia dotyczące zabezpieczeń obejmujące metadane
ms.date: 03/30/2017
ms.assetid: e78ef8ab-4f63-4656-ab93-b1deab2666d5
ms.openlocfilehash: c41ebf5c39e74932a4bade610c4e236b28444327
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601026"
---
# <a name="security-considerations-with-metadata"></a>Zagadnienia dotyczące zabezpieczeń obejmujące metadane
Korzystając z funkcji metadanych w programie Windows Communication Foundation (WCF), należy wziąć pod uwagę implikacje zabezpieczeń publikowania, pobierania i używania metadanych usługi.  
  
## <a name="when-to-publish-metadata"></a>Kiedy publikować metadane  
 Usługi WCF domyślnie nie publikują metadanych. Aby opublikować metadane dla usługi WCF, należy jawnie włączyć Publikowanie metadanych poprzez dodanie punktów końcowych metadanych do usługi (zobacz [Publikowanie metadanych](publishing-metadata.md)). Pozostawienie wyłączonego publikowania metadanych zmniejsza obszar ataków dla usługi i obniża ryzyko przypadkowego ujawnienia informacji. Nie wszystkie usługi muszą publikować metadane. Jeśli nie ma potrzeby publikowania metadanych, rozważ pozostawienie jej wyłączone. Należy pamiętać, że nadal można generować metadane i kod klienta bezpośrednio z zestawów usług przy użyciu [Narzędzia do obsługi metadanych ServiceModel (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md). Aby uzyskać więcej informacji o używaniu programu Svcutil. exe do eksportowania metadanych, zobacz [How to: use Svcutil. exe do eksportowania metadanych z skompilowanego kodu usługi](how-to-use-svcutil-exe-to-export-metadata-from-compiled-service-code.md).  
  
## <a name="publishing-metadata-using-a-secure-binding"></a>Publikowanie metadanych przy użyciu bezpiecznego powiązania  
 Domyślne powiązania metadanych udostępniane przez funkcję WCF nie są bezpieczne i umożliwiają dostęp anonimowy do metadanych. Metadane usługi publikowane przez usługę WCF zawierają szczegółowy opis usługi i mogą celowo lub przypadkowo zawierać informacje poufne. Na przykład metadane usługi mogą zawierać informacje o operacjach infrastruktury, które nie zostały zamierzone publicznie. Aby chronić metadane usługi przed nieautoryzowanym dostępem, można użyć bezpiecznego powiązania dla punktu końcowego metadanych. Punkty końcowe metadanych odpowiadają na żądania HTTP/GET, które mogą używać SSL (SSL) do zabezpieczania metadanych. Aby uzyskać więcej informacji, zobacz [jak: Zabezpieczanie punktów końcowych metadanych](how-to-secure-metadata-endpoints.md).  
  
 Zabezpieczanie punktów końcowych metadanych umożliwia żądającym bezpiecznego pobierania metadanych usługi bez ryzyka naruszenia lub fałszowania.  
  
## <a name="using-only-trusted-metadata"></a>Używanie tylko zaufanych metadanych  
 Metadanych usługi można użyć do automatycznego konstruowania składników czasu wykonywania wymaganych do wywołania usługi. Możesz również użyć metadanych w czasie projektowania, aby opracować aplikację kliencką lub w środowisku uruchomieniowym w celu dynamicznego aktualizowania powiązania używanego przez klienta do wywoływania usługi.  
  
 Metadane usługi mogą zostać naruszone lub sfałszowane po pobraniu w sposób niebezpieczny. Metadane naruszone mogą przekierować klienta do złośliwej usługi, zawierać ustawienia zabezpieczeń, które zostały naruszone, lub zawierają złośliwe struktury XML. Dokumenty metadanych mogą być duże i często zapisywane w systemie plików. Aby chronić przed manipulacją i fałszowaniem, należy użyć bezpiecznego powiązania do żądania metadanych usługi, gdy jest ona dostępna.  
  
## <a name="using-safe-techniques-for-processing-metadata"></a>Używanie bezpiecznych technik przetwarzania metadanych  
 Metadane usługi są często pobierane z usługi za pośrednictwem sieci przy użyciu standardowych protokołów, takich jak WS-MetadataExchange (MEX). Wiele formatów metadanych obejmuje mechanizmy odwołujące się do dodatkowych metadanych. <xref:System.ServiceModel.Description.MetadataExchangeClient>Typ automatycznie przetwarza odwołania w dokumentach Web Services Description Language (WSDL), schemacie XML i dokumentach Mex. Rozmiar <xref:System.ServiceModel.Description.MetadataSet> obiektu utworzonego na podstawie pobranych metadanych jest bezpośrednio proporcjonalny do <xref:System.ServiceModel.Description.MetadataExchangeClient.MaximumResolvedReferences%2A> wartości <xref:System.ServiceModel.Description.MetadataExchangeClient> użytego wystąpienia oraz `MaxReceivedMessageSize` wartości powiązania używanej przez to <xref:System.ServiceModel.Description.MetadataExchangeClient> wystąpienie. Ustaw te przydziały na odpowiednie wartości zgodnie z oczekiwaniami.  
  
 W programie WCF metadane usługi są przetwarzane w formacie XML. W przypadku przetwarzania dokumentów XML aplikacje powinny chronić się przed złośliwymi strukturami XML. Użyj programu <xref:System.Xml.XmlDictionaryReader> z odpowiednimi przydziałami podczas przetwarzania kodu XML, a także Ustaw <xref:System.Xml.XmlTextReader.DtdProcessing%2A> Właściwość na <xref:System.Xml.DtdProcessing.Prohibit> .  
  
 System metadanych w programie WCF jest rozszerzalny, a rozszerzenia metadanych można zarejestrować w pliku konfiguracyjnym aplikacji (zobacz [Rozszerzanie systemu metadanych](../extending/extending-the-metadata-system.md)). Rozszerzenia metadanych mogą uruchamiać dowolny kod, więc należy chronić plik konfiguracyjny aplikacji przy użyciu odpowiednich list kontroli dostępu (ACL) i rejestrować tylko implementacje zaufanych rozszerzeń metadanych.  
  
## <a name="validating-generated-clients"></a>Weryfikowanie wygenerowanych klientów  
 Podczas generowania kodu klienta z metadanych pobranych z niezaufanego źródła Sprawdź poprawność wygenerowanego kodu klienta, aby upewnić się, że wygenerowany klient jest zgodny z zasadami zabezpieczeń aplikacji klienckich. Aby sprawdzić ustawienia powiązania klienta lub wizualnie zbadać kod generowany przez narzędzia, można użyć zachowania weryfikacji. Aby zapoznać się z przykładem sposobu implementacji klienta sprawdzającego zachowania, zobacz [Walidacja klienta](../samples/client-validation.md).  
  
## <a name="protecting-application-configuration-files"></a>Ochrona plików konfiguracji aplikacji  
 Plik konfiguracji aplikacji usługi może określać, jak i czy metadane są publikowane. Dobrym pomysłem jest ochronę pliku konfiguracyjnego aplikacji przy użyciu odpowiednich list kontroli dostępu (ACL), aby upewnić się, że osoba atakująca nie może zmodyfikować takich ustawień.  
  
## <a name="see-also"></a>Zobacz też

- [Instrukcje: bezpieczne punkty końcowe metadanych](how-to-secure-metadata-endpoints.md)
- [Bezpieczeństwo](security.md)

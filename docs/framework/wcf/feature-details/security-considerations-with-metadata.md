---
title: Zagadnienia dotyczące zabezpieczeń obejmujące metadane
ms.date: 03/30/2017
ms.assetid: e78ef8ab-4f63-4656-ab93-b1deab2666d5
ms.openlocfilehash: 0dc060475f868923e8c7e4c87ef43ef5912c7ac5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59172968"
---
# <a name="security-considerations-with-metadata"></a>Zagadnienia dotyczące zabezpieczeń obejmujące metadane
Korzystając z funkcji metadanych w Windows Communication Foundation (WCF), należy wziąć pod uwagę ryzyko związane z publikowania, pobieranie i używanie usług metadanych.  
  
## <a name="when-to-publish-metadata"></a>Podczas publikowania metadanych  
 Usługi WCF nie należy również publikować metadane domyślnie. Publikowanie metadanych dla usługi WCF, musisz jawnie włączyć publikowanie metadanych przez dodanie punktów końcowych metadanych z usługą (zobacz [Publikowanie metadanych](../../../../docs/framework/wcf/feature-details/publishing-metadata.md)). Pozostawienie Publikowanie metadanych wyłączone zmniejsza możliwości zaatakowania dla Twojej usługi i zmniejsza ryzyko ujawnienia informacji niezamierzone. Nie wszystkie usługi, należy opublikować metadanych. Jeśli nie masz Publikowanie metadanych, należy wziąć pod uwagę pozostawić go wyłączyć. Należy pamiętać, że istnieje możliwość wygenerowania kodu metadanych i klient nadal bezpośrednio z zestawów przy użyciu usługi [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). Aby uzyskać więcej informacji o używaniu Svcutil.exe, aby wyeksportować metadane, zobacz [jak: Eksportowanie metadanych ze skompilowanego kodu usługi za pomocą Svcutil.exe](../../../../docs/framework/wcf/feature-details/how-to-use-svcutil-exe-to-export-metadata-from-compiled-service-code.md).  
  
## <a name="publishing-metadata-using-a-secure-binding"></a>Publikowanie metadanych przy użyciu bezpiecznego powiązania  
 Domyślne powiązania metadanych, udostępnianych przez usługi WCF nie są bezpieczne i zezwolić na dostęp anonimowy do metadanych. Metadane usługi, która umożliwia publikowanie usług WCF zawiera szczegółowy opis dotyczących usługi i mogą celowo lub przypadkowo zawierać informacje poufne. Na przykład metadane usługi mogą zawierać informacje o operacjach infrastruktury, która nie jest przeznaczony do emisji publicznie. Aby chronić metadanych usługi przed nieautoryzowanym dostępem, można użyć bezpiecznego powiązania dla punktu końcowego metadanych. Punkty końcowe metadanych odpowiadać na żądania HTTP/GET, które umożliwiają zabezpieczanie metadanych Secure Sockets Layer (SSL). Aby uzyskać więcej informacji, zobacz [jak: Bezpieczne punkty końcowe metadanych](../../../../docs/framework/wcf/feature-details/how-to-secure-metadata-endpoints.md).  
  
 Zabezpieczanie punktów końcowych metadanych także sposób dla stron żądających certyfikatów do bezpiecznego pobierania metadanych usługi bez ryzyka stałego skanowania włamania lub fałszowanie adresów.  
  
## <a name="using-only-trusted-metadata"></a>Tylko przy użyciu zaufanego metadanych  
 Metadane usługi służy do automatycznego tworzenia składników środowiska wykonawczego, wymaganych do wywołania tej usługi. Umożliwia także metadanych w czasie projektowania do tworzenia aplikacji klienckiej lub w czasie wykonywania, aby dynamicznie aktualizować powiązanie klient używa do wywołania usługi.  
  
 Metadane usługi mogą być naruszone lub sfałszowane podczas pobierania w niezabezpieczony sposób. Zmodyfikowany metadanych można przekierowania klienta z usługą złośliwe, zawierają ustawienia, których bezpieczeństwo zostało naruszone bezpieczeństwo lub zawierać złośliwego struktury XML. Dokumenty metadanych mogą być duże i często są zapisywane w systemie plików. Aby chronić przed naruszeniem i fałszowania, Użyj bezpiecznego powiązania żądanie metadanych usługi, gdy jest on dostępny.  
  
## <a name="using-safe-techniques-for-processing-metadata"></a>Przy użyciu bezpiecznych technik przetwarzania metadanych  
 Metadane usługi są często pobierane z usługi za pośrednictwem sieci przy użyciu standardowych protokołów, takich jak usługi WS-MetadataExchange (MEX). Wiele formatów metadane obejmują odwołujące się do mechanizmy wskazuje dodatkowe metadane. <xref:System.ServiceModel.Description.MetadataExchangeClient> Typu automatycznie przetwarza odwołania dla Ciebie w dokumentach sieci Web Services Description Language (WSDL), schematu XML i MEX dokumentów. Rozmiar <xref:System.ServiceModel.Description.MetadataSet> obiektu utworzonego na podstawie metadanych pobrane jest wprost proporcjonalna do <xref:System.ServiceModel.Description.MetadataExchangeClient.MaximumResolvedReferences%2A> wartość <xref:System.ServiceModel.Description.MetadataExchangeClient> wystąpienia, która jest używana i `MaxReceivedMessageSize` wartość do powiązania, używany przez to <xref:System.ServiceModel.Description.MetadataExchangeClient> wystąpienia. Ustaw te przydziały odpowiednie wartości zgodnie z ustawieniem danego scenariusza.  
  
 W programie WCF metadane usługi są przetwarzane w formacie XML. Podczas przetwarzania dokumentów XML, aplikacje powinny ochrony przed złośliwymi struktury XML. Użyj <xref:System.Xml.XmlDictionaryReader> z odpowiednie limity przydziału podczas przetwarzania XML, a także ustawić <xref:System.Xml.XmlTextReader.DtdProcessing%2A> właściwość <xref:System.Xml.DtdProcessing.Prohibit>.  
  
 System metadanych w programie WCF jest wszechstronne i metadanych rozszerzeń mogą być rejestrowane w pliku konfiguracyjnym aplikacji (zobacz [rozszerzanie systemu metadanych](../../../../docs/framework/wcf/extending/extending-the-metadata-system.md)). Metadane rozszerzenia może uruchomić dowolny kod, dlatego powinna zapewniać ochronę pliku konfiguracji aplikacji przy użyciu kontroli dostępu odpowiednie list kontroli dostępu (ACL) i zarejestrować tylko metadane zaufanego rozszerzenia implementacji.  
  
## <a name="validating-generated-clients"></a>Sprawdzanie poprawności wygenerowanego klientów  
 Podczas generowania kodu klienta z metadanych pobranego ze źródła, który nie jest zaufany, sprawdź poprawność kodu wygenerowanego klienta, aby upewnić się, że wygenerowanego klienta spełnia zasady zabezpieczeń dla aplikacji klienckich. Sprawdzanie poprawności zachowanie służy do ustawienia na komputerze klienckim powiązanie lub wizualnie badać kod wygenerowany przez narzędzia. Na przykład sposób implementacji klienta, która weryfikuje zachowania zobacz [sprawdzanie poprawności klienta](../../../../docs/framework/wcf/samples/client-validation.md).  
  
## <a name="protecting-application-configuration-files"></a>Ochrona plików konfiguracji aplikacji  
 Plik konfiguracji aplikacji usługi mogą kontrolować sposób i publikowane są metadane. To dobry pomysł, aby chronić plik konfiguracyjny aplikacji przy użyciu list kontroli dostępu (ACL), aby upewnić się, że osoba atakująca nie można modyfikować tych ustawień.  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: Bezpieczne punkty końcowe metadanych](../../../../docs/framework/wcf/feature-details/how-to-secure-metadata-endpoints.md)
- [Zabezpieczenia](../../../../docs/framework/wcf/feature-details/security.md)

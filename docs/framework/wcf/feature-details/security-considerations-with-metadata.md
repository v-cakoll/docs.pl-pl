---
title: Zagadnienia dotyczące zabezpieczeń obejmujące metadane
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e78ef8ab-4f63-4656-ab93-b1deab2666d5
caps.latest.revision: 10
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload:
- dotnet
ms.openlocfilehash: 393730ffe57c4678f53d16e67b8b8f64ad16509c
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/30/2018
---
# <a name="security-considerations-with-metadata"></a>Zagadnienia dotyczące zabezpieczeń obejmujące metadane
Jeśli przy użyciu metadanych funkcji w [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)], należy wziąć pod uwagę ryzyko związane z publikowania, pobieranie i przy użyciu usługi metadanych.  
  
## <a name="when-to-publish-metadata"></a>Podczas publikowania metadanych  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi nie Publikowanie metadanych domyślnie. Publikowanie metadanych dla [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi, musisz jawnie włączyć publikowanie metadanych przez dodanie punkty końcowe metadanych z usługą (zobacz [Publikowanie metadanych](../../../../docs/framework/wcf/feature-details/publishing-metadata.md)). Pozostawienie Publikowanie metadanych wyłączone zmniejsza możliwości ataku usługi i zmniejsza ryzyko ujawnienia informacji przypadkowe. Nie wszystkie usługi należy opublikować metadanych. Jeśli nie masz Publikowanie metadanych, należy wziąć pod uwagę pozostawić go wyłączyć. Należy pamiętać, że istnieje możliwość wygenerowania kodu metadanych i klient nadal bezpośrednio z z zestawów usługi przy użyciu [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). Aby uzyskać więcej informacji o używaniu Svcutil.exe do wyeksportowania metadanych, zobacz [porady: użycie Svcutil.exe Eksportowanie metadanych ze skompilowanego kodu usługi](../../../../docs/framework/wcf/feature-details/how-to-use-svcutil-exe-to-export-metadata-from-compiled-service-code.md).  
  
## <a name="publishing-metadata-using-a-secure-binding"></a>Publikowanie metadanych za pomocą bezpiecznego powiązania  
 Powiązania metadanych domyślne który [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zapewnia nie zabezpieczyć i zezwalają na dostęp anonimowy do metadanych. Metadane usługi który [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi zawiera szczegółowy opis dotyczących usługi i mogą celowo lub przypadkowo zawierać informacje poufne. Na przykład metadane usługi mogą zawierać informacje o operacjach infrastruktury, która nie ma to być publicznie emisji. Aby chronić metadanych usługi przed nieautoryzowanym dostępem, można użyć bezpiecznego powiązania dla punktu końcowego metadanych. Punkty końcowe metadanych odpowiadać na żądania HTTP/GET, które umożliwiają Secure Sockets Layer (SSL) do zabezpieczania metadanych. Aby uzyskać więcej informacji, zobacz [porady: Zabezpieczanie punktów końcowych metadanych](../../../../docs/framework/wcf/feature-details/how-to-secure-metadata-endpoints.md).  
  
 Zabezpieczanie punktów końcowych metadanych także sposób dla jednostek żądających bezpieczne pobieranie metadanych usługi bez ryzyka naruszeniu lub fałszowania.  
  
## <a name="using-only-trusted-metadata"></a>Tylko przy użyciu zaufanego metadanych  
 Metadane usługi służy do automatycznego tworzenia składników środowiska wykonawczego, wymaganych do wywołania tej usługi. Umożliwia także metadanych w czasie projektowania umożliwiające tworzenie aplikacji klienckich, lub w czasie wykonywania, aby dynamicznie aktualizować powiązania klient używa do wywołania usługi.  
  
 Metadane usługi mogą przez osoby niepowołane lub sfałszowane po pobraniu w sposób niezabezpieczonych. Zmodyfikowany metadanych można przekierować klienta do usługi złośliwego, zawierają ustawienia, którego bezpieczeństwo zostało naruszone zabezpieczenia lub zawierać złośliwe struktury XML. Dokumentów metadanych może być duży i często są zapisywane w systemie plików. Aby zapewnić ochronę przed naruszeniem i fałszowania, używa bezpiecznego powiązania do żądania metadanych usługi, jeśli jest dostępny.  
  
## <a name="using-safe-techniques-for-processing-metadata"></a>Przy użyciu technik bezpiecznego przetwarzania metadanych  
 Metadane usługi często są pobierane z usługi za pośrednictwem sieci przy użyciu standardowych protokołów, takich jak usługi WS-MetadataExchange (MEX). Wiele formatów metadane obejmują odwołujące się do mechanizmów wskazuje dodatkowe metadane. <xref:System.ServiceModel.Description.MetadataExchangeClient> Typu automatycznie przetwarza odwołań dla Ciebie w dokumentach Web Services Description Language (WSDL), schemat XML i MEX dokumentów. Rozmiar <xref:System.ServiceModel.Description.MetadataSet> obiekt utworzony z metadanych pobranych jest wprost proporcjonalny do <xref:System.ServiceModel.Description.MetadataExchangeClient.MaximumResolvedReferences%2A> wartość <xref:System.ServiceModel.Description.MetadataExchangeClient> wystąpienie, które jest używane i `MaxReceivedMessageSize` wartość używana przez to powiązanie <xref:System.ServiceModel.Description.MetadataExchangeClient> wystąpienia. Ustaw te przydziały odpowiednie wartości zgodnie z ustawieniem danego scenariusza.  
  
 W [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], metadane usługi jest przetwarzany jako XML. Podczas przetwarzania dokumentów XML, aplikacji powinna zapewniać ochronę się przed złośliwymi struktury XML. Użyj `XmlDictionaryReader` z odpowiednimi przydziały podczas przetwarzania kodu XML, a także ustawić <xref:System.Xml.XmlTextReader.DtdProcessing%2A> właściwości `Prohibit`.  
  
 System metadanych w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] rozszerzać i rozszerzenia metadane mogą być rejestrowane w pliku konfiguracji aplikacji (zobacz [rozszerzanie systemu metadanych](../../../../docs/framework/wcf/extending/extending-the-metadata-system.md)). Rozszerzenia metadanych można uruchomić dowolny kod, więc powinna zapewniać ochronę pliku konfiguracji aplikacji przy użyciu kontroli dostępu w odpowiedniej list kontroli dostępu (ACL) i zarejestruj implementacje rozszerzenia tylko metadane zaufanych.  
  
## <a name="validating-generated-clients"></a>Sprawdzanie poprawności wygenerowanego klientów  
 Podczas generowania kodu klienta z metadanych pobrane ze źródła, który nie jest zaufany, sprawdź poprawność kodu wygenerowanego klienta, aby upewnić się, że wygenerowanego klienta odpowiada zasady zabezpieczeń aplikacji klienta. Sprawdzanie poprawności zachowanie umożliwia ustawienia na komputerze klienckim powiązanie lub wizualnie Przejrzyj kod wygenerowany przez narzędzia. Na przykład sposobu wdrażania klienta, która weryfikuje zachowania zobacz [weryfikacji klienta](../../../../docs/framework/wcf/samples/client-validation.md).  
  
## <a name="protecting-application-configuration-files"></a>Ochrona pliki konfiguracji aplikacji  
 Plik konfiguracji usługi aplikacji może kontrolować sposób i jeśli jest publikowany w metadanych. Zaleca ochronę pliku konfiguracji aplikacji przy użyciu list kontroli dostępu (ACL), aby upewnić się, że osoba atakująca nie można modyfikować tych ustawień.  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: bezpieczne punkty końcowe metadanych](../../../../docs/framework/wcf/feature-details/how-to-secure-metadata-endpoints.md)  
 [Zabezpieczenia](../../../../docs/framework/wcf/feature-details/security.md)

---
title: Przegląd integrowania z aplikacjami COM+
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, COM+ integration
- WCF, COM+ integration
ms.assetid: e481e48f-7096-40eb-9f20-7f0098412941
ms.openlocfilehash: 708c23f80dc3ed0a5b134295a16a20747d555be4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54492341"
---
# <a name="integrating-with-com-applications-overview"></a>Przegląd integrowania z aplikacjami COM+
Windows Communication Foundation (WCF) zapewnia bogate środowisko tworzenia aplikacji rozproszonych. Jeśli już używasz logiki oparty na komponentach aplikacji hostowanej w modelu COM +, można użyć programu WCF do rozszerzenia Twojej istniejącej logiki, a nie po prostu go do. Typowym scenariuszem jest, gdy chcesz udostępnić istniejącej logiki biznesowej modelu COM + lub korporacyjnych usług za pośrednictwem usług sieci Web.  
  
 Gdy interfejs składnika COM + jest widoczny jako usługi sieci Web, Specyfikacja i umowy te usługi są określane przez automatyczne mapowanie, które jest wykonywane w czasie inicjowania aplikacji. Na poniższej liście przedstawiono modelu koncepcyjnego dla tego mapowania:  
  
-   Jedna usługa jest zdefiniowana dla każdej narażonych klasy COM.  
  
-   Kontrakt usługi pochodzi bezpośrednio z definicji interfejsu wybranego składnika, z możliwością wyłączenia metody zdefiniowane w konfiguracji.  
  
-   Operacje w tej Umowy są uzyskiwane bezpośrednio z metod w definicji interfejsu składnika.  
  
-   Parametry te operacje są wyprowadzane bezpośrednio z typu współdziałania COM, który odnosi się do składnika parametrów metody.  
  
 Domyślny adres i powiązania transportu dla usługi znajdują się w pliku konfiguracji usługi, ale są ponownie skonfigurowane jako wymagane.  
  
> [!NOTE]
>  Kontrakty dotyczące uwidocznionych usług sieci Web pozostaje niezmienna, tak długo, jak interfejsy modelu COM + i konfiguracji pozostają niezmienione. Modyfikacja kilka interfejsów nie jest aktualizowane automatycznie dostępne usługi i wymaga ponownego uruchamiania narzędzia konfiguracji modelu usług COM + (ComSvcConfig.exe).  
  
 Wymagania dotyczące uwierzytelniania i autoryzacji w aplikacji COM + i jego składników w dalszym ciągu wymuszane, gdy jest używana jako usługę sieci Web.  
  
 Jeżeli obiekt wywołujący inicjuje transakcja usługi sieci Web, składniki oznaczone jako transakcyjnych zarejestrować się w tym zakresie transakcji.  
  
 Poniższe kroki są wymagane do udostępnienia interfejs składnika COM + jako usługę sieci Web bez konieczności modyfikacji składnika:  
  
1.  Ustal, czy interfejs składnika COM + mogą udostępniony jako usługa sieci Web.  
  
2.  Wybierz odpowiedni tryb hostingu.  
  
3.  Aby dodać usługę sieci Web dla interfejsu, należy użyć narzędzia konfiguracji modelu usług COM + (ComSvcConfig.exe). Aby uzyskać więcej informacji o sposobie używania ComSvcConfig.exe, zobacz [jak: Używanie narzędzia konfiguracji modelu usług COM +](../../../../docs/framework/wcf/feature-details/how-to-use-the-com-service-model-configuration-tool.md).  
  
4.  Skonfiguruj ustawienia dodatkowe usługi w pliku konfiguracyjnym aplikacji. Aby uzyskać więcej informacji na temat konfigurowania składnika zobacz [jak: Konfigurowanie ustawień usługi COM +](../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md).  
  
## <a name="supported-interfaces"></a>Obsługiwanymi interfejsami  
 Istnieją pewne ograniczenia dotyczące typów interfejsów, które są dostępne jako usługę sieci Web. Następujące typy interfejsów nie są obsługiwane:  
  
-   Interfejsy, które przekazuj odwołania do obiektów jako parametrów - następujące podejście odwołanie do obiektu ograniczony zostanie omówione w sekcji ograniczoną obsługę odwołanie do obiektu.  
  
-   Interfejsy, które przekazywania typów, które nie są zgodne z [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] konwersje współdziałania COM.  
  
-   Interfejsy na potrzeby aplikacji, które mają włączone w przypadku hostowania w modelu COM + Tworzenie pul aplikacji.  
  
-   Interfejsy składników, które są oznaczone jako prywatne do aplikacji.  
  
-   Infrastruktura interfejsów modelu COM +.  
  
-   Interfejsy z poziomu aplikacji systemu.  
  
-   Interfejsy ze składników usług dla przedsiębiorstw, które nie zostały dodane do globalnej pamięci podręcznej.  
  
### <a name="limited-object-reference-support"></a>Obsługa odwołań ograniczonych obiektów  
 Ponieważ liczba składników modelu COM + wdrożone za pomocą obiektów parametrów odwołania, na przykład zwraca obiekt zestawu rekordów ADO integracja modelu COM + zawiera ograniczoną obsługę parametrów odwołanie do obiektu. Obsługa jest ograniczona do obiektów, które implementują `IPersistStream` interfejsu COM. Obejmuje obiekty zestawu rekordów ADO i można zaimplementować dla obiektów COM z określonych aplikacji.  
  
 Aby włączyć obsługę tego, udostępnia narzędzia ComSvcConfig.exe **allowreferences** przełącznika, który powoduje wyłączenie parametru podpis metody regularnego i sprawdza, czy działa narzędzie, aby upewnić się, że nie są używane parametry odwołanie do obiektu . Ponadto, typy obiektów, które są przekazywane jako parametry należy o nazwie i zidentyfikowane w ciągu <`persistableTypes`> element konfiguracji, który jest elementem podrzędnym <`comContract`> element.  
  
 Gdy ta funkcja jest używana, używa usługi integracji COM + `IPersistStream` interfejsu do serializacji lub deserializacji wystąpienia obiektu. Jeśli wystąpienie obiektu nie obsługuje `IPersistStream`, zgłaszany jest wyjątek.  
  
 W aplikacji klienckiej, metody na <xref:System.ServiceModel.ComIntegration.PersistStreamTypeWrapper> obiekt może być używany do przekazania obiektu w usłudze i podobnie można pobrać obiektu.  
  
> [!NOTE]
>  Ze względu na charakter niestandardowej i specyficzne dla platformy podejście serializacji jest najlepszym rozwiązaniem w przypadku użycia między klientami programu WCF i usługi WCF.  
  
## <a name="selecting-the-hosting-mode"></a>Wybieranie trybu hostingu  
 COM + uwidacznia usług sieci Web na jeden z następujących trybów hostingu:  
  
-   COM+-hosted  
  
     Usługa sieci Web jest hostowana w ramach aplikacji dedykowanego modelu COM + procesu serwera (Dllhost.exe). Ten tryb wymaga aplikacji, aby jawnie uruchomić przed może odbierać żądania usługi sieci Web. COM + opcji "Uruchom jako usługa NT" lub "Pozostaw uruchomiony podczas bezczynności" może służyć do uniemożliwić bezczynności zamknięcie aplikacji i usług. Ten tryb zapewnia usługi sieci Web i dostępu DCOM dla aplikacji serwera.  
  
-   Hostowane w sieci Web  
  
     Usługa sieci Web jest hostowana w ramach procesu roboczego serwera sieci Web. Ten tryb nie wymaga modelu COM + na aktywny, po odebraniu początkowego żądania. Jeśli aplikacja nie jest aktywny, po odebraniu tego żądania, automatycznie została aktywowana przed rozpoczęciem przetwarzania żądania. W tym trybie również zapewnia usługi sieci Web i dostępu DCOM dla aplikacji serwera, ale powoduje, że przeskoku proces w przypadku żądań usług sieci Web. Wymaga to zazwyczaj kliencie, aby umożliwić personifikacji. W programie WCF, można to zrobić za pomocą <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> właściwość <xref:System.ServiceModel.Security.WindowsClientCredential> klasy, który jest dostępny jako właściwość ogólnego <xref:System.ServiceModel.ChannelFactory%601> klasy, jak również <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation> wartość wyliczenia.  
  
-   Hostowane w sieci Web w procesie  
  
     Usługa sieci Web i logiki aplikacji modelu COM + znajdują się w ramach procesu roboczego serwera sieci Web. Zapewnia to automatyczną aktywację w trybie hostowanej w sieci Web bez powodowania przeskoku proces w przypadku żądań usług sieci Web. Wadą jest to, że aplikacja serwera nie są dostępne za pośrednictwem modelu DCOM.  
  
### <a name="security-considerations"></a>Zagadnienia dotyczące zabezpieczeń  
 Podobnie jak inne usługi WCF ustawienia zabezpieczeń dla narażonych usługi są zarządzane za pomocą ustawień konfiguracji dla kanału WCF. Tradycyjne ustawień zabezpieczeń modelu DCOM, takich jak ustawienia uprawnień dla komputera modelu DCOM nie są wymuszane. Aby wymusić ról aplikacji modelu COM +, autoryzacji "kontroli dostępu na poziomie składnika" musi być włączona dla tego składnika.  
  
 Korzystanie z powiązania niezabezpieczonych można pozostawić komunikacji otwarte do manipulowania lub ujawnienie informacji. Aby temu zapobiec, zaleca się, że używasz bezpiecznego powiązania.  
  
 Dla modelu COM +-tryby hostowanej, która jest hostowana w sieci Web, aplikacje klienckie należy zezwolić na działanie procesu serwera personifikować użytkownika klienta. Można to zrobić w klientach usługi WCF, ustawiając poziom personifikacji <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>.  
  
 Za pomocą usług Internet Information Services (IIS) lub Windows Process Activation Service (WAS) przy użyciu protokołu HTTP narzędzia Httpcfg.exe może służyć do rezerwowania adresu punktu końcowego transportu. W innych konfiguracjach jest ważne, aby zapewnić ochronę przed usług nieautoryzowany, które działają jako zamierzone usługi. Aby uniemożliwić nieautoryzowane usługi zaczynając od żądanego punktu końcowego, uzasadnione usługi można skonfigurować do uruchamiania jako usługi NT. Dzięki temu uzasadnione usługi oświadczenie adresu punktu końcowego przed dowolnych usług nieautoryzowany.  
  
 Podczas udostępniania aplikacji modelu COM + o skonfigurowanych ról modelu COM + jako usługa hostowana w sieci Web, "Uruchom usługi IIS konto procesu", należy dodać do jednej z ról aplikacji. To konto, zwykle o nazwie IWAM_machinename, należy dodać umożliwia zamknięcie czyste obiektów po użyciu. To konto nie może być przyznany dodatkowych uprawnień.  
  
 Nie można użyć modelu COM + odtwarzanie procesów funkcji w zintegrowanej aplikacji. Jeśli aplikacja jest skonfigurowana do użycia, odtwarzanie procesów i składniki są uruchomione w procesie hostowanych modelu COM +, nie można uruchomić usługi. To wymaganie nie obejmuje usług przy użyciu trybu w trakcie hostowanych w sieci Web, ponieważ nie są stosowane ustawienia odtwarzania procesu.  
  
## <a name="see-also"></a>Zobacz także
- [Przegląd integrowania z aplikacjami COM](../../../../docs/framework/wcf/feature-details/integrating-with-com-applications-overview.md)

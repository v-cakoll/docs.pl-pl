---
title: Przegląd integrowania z aplikacjami COM+
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, COM+ integration
- WCF, COM+ integration
ms.assetid: e481e48f-7096-40eb-9f20-7f0098412941
ms.openlocfilehash: 155365c72fd3f5915db12104f45a500f3176f67b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="integrating-with-com-applications-overview"></a>Przegląd integrowania z aplikacjami COM+
Windows Communication Foundation (WCF) udostępnia bogate środowisko tworzenia aplikacji rozproszonych. Jeśli korzystasz już z logiki na podstawie składnika aplikacji hostowanej w modelu COM +, służy WCF do rozszerzenia istniejących logiki zamiast konieczności ponownego zapisania go. Typowy scenariusz obejmuje, gdy chcesz udostępnić istniejącego modelu COM + lub usług dla przedsiębiorstw logiki biznesowej za pośrednictwem usług sieci Web.  
  
 Gdy interfejs składnika COM + jest udostępniany jako usługa sieci Web, Specyfikacja i kontraktu usługi te są określane przez automatyczne mapowanie, które jest przeprowadzane w czasie inicjowania aplikacji. Na poniższej liście przedstawiono modelu koncepcyjnego dla tego mapowania:  
  
-   Jedna usługa jest zdefiniowany dla każdego dostępnego klasy COM.  
  
-   Kontrakt usługi pochodzi bezpośrednio z definicji interfejsu wybranego składnika, z możliwością metody wykluczeń zdefiniowanych w konfiguracji.  
  
-   Operacje tego kontraktu są pochodzi bezpośrednio z metod w definicji interfejsu składnika.  
  
-   Parametry te operacje są pochodzi bezpośrednio z typu współdziałania COM odpowiadającego składnika parametry metody.  
  
 Domyślne adresy i powiązania transportu dla usługi znajdują się w pliku konfiguracji usługi, ale można je można ponownie skonfigurować jako wymagane.  
  
> [!NOTE]
>  Kontrakty narażonych usług sieci Web pozostają takie same jak interfejsów modelu COM + i konfiguracja pozostają niezmienione. Modyfikacja kilka interfejsów nie jest aktualizowana automatycznie dostępnych usług i wymaga ponownego uruchamiania narzędzia konfiguracji modelu usług COM + (ComSvcConfig.exe).  
  
 Wymagania dotyczące uwierzytelniania i autoryzacji aplikacji COM + i jej elementów nadal mają być egzekwowane, gdy jest używany jako usługę sieci Web.  
  
 Jeśli element wywołujący inicjuje transakcję usługi sieci Web, składniki oznaczona jako transakcyjne zarejestrować się w obrębie tej transakcji.  
  
 Poniższe kroki są wymagane do udostępnienia interfejs składnika COM + jako usługę sieci Web bez konieczności modyfikacji składnika:  
  
1.  Ustal, czy interfejs składnika COM + mogą być udostępniany jako usługi sieci Web.  
  
2.  Wybierz odpowiedni tryb obsługi.  
  
3.  Użyj narzędzia konfiguracji modelu usług COM + (ComSvcConfig.exe), aby dodać usługi sieci Web dla interfejsu. Aby uzyskać więcej informacji o sposobie używania ComSvcConfig.exe, zobacz [porady: Użyj modelu COM + narzędzia konfiguracji modelu usług](../../../../docs/framework/wcf/feature-details/how-to-use-the-com-service-model-configuration-tool.md).  
  
4.  Skonfiguruj ustawienia dodatkowe usługi w pliku konfiguracyjnym aplikacji. Aby uzyskać więcej informacji na temat konfigurowania składnika, zobacz [porady: Konfigurowanie ustawień usługi COM +](../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md).  
  
## <a name="supported-interfaces"></a>Interfejsy obsługiwane  
 Istnieją pewne ograniczenia dotyczące typów interfejsów, które są dostępne jako usługę sieci Web. Następujące typy interfejsów nie są obsługiwane:  
  
-   Interfejsy, które są przekazywane jako parametry - odwołania do obiektów następujące podejście odwołanie do obiektu ograniczone jest opisana w sekcji ograniczoną obsługę odwołanie do obiektu.  
  
-   Interfejsy, które przekazywania typów, które nie są zgodne z [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] konwersje współdziałania COM.  
  
-   Interfejsy dla aplikacji, które mają aplikacji Buforowanie włączone, gdy obsługiwanych przez COM +.  
  
-   Interfejsy składników, które są oznaczone jako prywatne do aplikacji.  
  
-   Infrastruktura interfejsów modelu COM +.  
  
-   Interfejsy aplikacji system.  
  
-   Interfejsy ze składników usług dla przedsiębiorstw, które nie zostały dodane do pamięci podręcznej GAC.  
  
### <a name="limited-object-reference-support"></a>Obsługa odwołanie do obiektu ograniczone  
 Ponieważ liczba wdrożonych składniki modelu COM + za pomocą obiektów parametrów odwołania, takich jak zwracając obiekt zestawu rekordów ADO integracja modelu COM + obejmuje ograniczoną obsługę parametrów odwołanie do obiektu. Obsługa jest ograniczona do obiektów implementujących `IPersistStream` interfejsu COM. Obejmuje obiekty zestawu rekordów ADO i można stosować dla obiektów COM, określonych aplikacji.  
  
 Aby włączyć tę obsługę, zawiera narzędzie ComSvcConfig.exe **allowreferences** przełącznika, który powoduje wyłączenie parametru podpis metody regularnych i sprawdza, czy działa narzędzie, aby upewnić się, że nie są używane parametry odwołanie do obiektu . Ponadto należy o nazwie i w typy obiektów, które są przekazywane jako parametry <`persistableTypes`> element konfiguracji, który jest elementem podrzędnym elementu <`comContract`> elementu.  
  
 Gdy ta funkcja jest używana, używa usługi integracji COM + `IPersistStream` interfejs do serializacji lub deserializacji wystąpienia obiektu. Jeśli wystąpienie obiektu nie obsługuje `IPersistStream`, jest zgłaszany wyjątek.  
  
 W aplikacji klienta, metod na <xref:System.ServiceModel.ComIntegration.PersistStreamTypeWrapper> obiekt może służyć do przekazania do obiektu w usłudze i podobnie można pobrać obiektu.  
  
> [!NOTE]
>  Ze względu na specyfikę specyficzne dla platformy i niestandardowych podejścia serializacji jest najodpowiedniejsze do użytku między klientami programu WCF i usługi WCF.  
  
## <a name="selecting-the-hosting-mode"></a>Wybieranie trybu hostingu  
 COM + udostępnia usługi sieci Web w jednej z następujących trybów hostingu:  
  
-   COM +-hostowanej  
  
     Usługa sieci Web znajduje się w obrębie aplikacji dedykowanych COM + procesu serwera (Dllhost.exe). Ten tryb wymaga, aby jawnie uruchomić przed może odbierać żądania usługi sieci Web aplikacja. COM + opcji "Uruchom jako usługa NT" lub "Pozostaw uruchomiony podczas bezczynności" można zapobiec bezczynności zamknięcia aplikacji i jej usług. Ten tryb zapewnia usługi sieci Web i dostępu DCOM dla aplikacji serwera.  
  
-   Hostowana w sieci Web  
  
     Usługa sieci Web jest obsługiwana w ramach procesu roboczego serwera sieci Web. Ten tryb nie wymaga modelu COM + jest aktywne po odebraniu żądania początkowego. Jeśli aplikacja nie jest aktywne po odebraniu tego żądania, jest automatycznie aktywowane przed przetworzeniem żądania. Ten tryb również zapewnia usługi sieci Web i dostępu DCOM dla aplikacji serwera, ale powoduje, że proces przeskoków dla żądania usługi sieci Web. Wymaga to zwykle Włącz personifikację klienta. W programie WCF, można to zrobić z <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> właściwość <xref:System.ServiceModel.Security.WindowsClientCredential> klasy, która jest dostępna jako właściwość ogólnego <xref:System.ServiceModel.ChannelFactory%601> klasy, jak również <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation> wartości wyliczenia.  
  
-   Sieci Web hostowanych w procesie  
  
     Usługi sieci Web i logiki aplikacji COM + znajdują się w obrębie procesu roboczego serwera sieci Web. Zapewnia to automatyczną aktywację w trybie hostowanej przez sieci Web bez powodowania przeskok procesu dla żądania usługi sieci Web. Wadą jest to, czy aplikacja serwera nie jest dostępna za pośrednictwem modelu DCOM.  
  
### <a name="security-considerations"></a>Zagadnienia dotyczące zabezpieczeń  
 Podobnie jak inne usługi WCF ustawienia zabezpieczeń dla usługi narażonych są zarządzane za pomocą ustawień konfiguracji dla kanału WCF. Tradycyjny ustawienia zabezpieczeń modelu DCOM, takie jak ustawienia komputera uprawnień modelu DCOM nie są wymuszane. Aby wymusić ról aplikacji COM +, autoryzacji "kontroli dostępu na poziomie składnika" musi być włączony dla składnika.  
  
 Używanie powiązania nie są zabezpieczone można pozostawić komunikacji Otwórz do manipulowania lub ujawnienie informacji. Aby tego uniknąć, zaleca się użycie bezpiecznego powiązania.  
  
 Dla modelu COM +-tryby hostowanej i hostowanych w sieci Web, aplikacje klienckie muszą zezwalać na proces serwera można personifikować użytkownika klienta. Można to zrobić w klientach WCF przez ustawienie poziomu personifikacji <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>.  
  
 Internet Information Services (IIS) lub Windows Process Activation Service (WAS) przy użyciu protokołu HTTP narzędzia Httpcfg.exe można zastrzec adresu punktu końcowego transportu. W innych konfiguracji należy zapewnić ochronę przed nieautoryzowanych usług, które działa jako usługa przeznaczone. Aby zapobiec zaczynając od żądanego punktu końcowego usługi nieautoryzowanego, uzasadnionych usługi można skonfigurować do uruchamiania jako usługa NT. Dzięki temu uzasadnionych usługi do oświadczeń adres punktu końcowego przed żadnych usług nieautoryzowany.  
  
 Jeśli udostępnianie aplikacji COM + z skonfigurowanych ról COM + jako usługa hostowana w sieci Web, "Uruchamianie usługi IIS konto procesu" musisz dodać do jednej z ról aplikacji. To konto, zwykle o nazwie IWAM_machinename, należy dodać umożliwia zamknięcie czyste obiektów po użyciu. Konto nie należy przyznawać żadnych dodatkowych uprawnień.  
  
 Proces COM + odtwarzania funkcji nie można używać w zintegrowanej aplikacji. Jeśli aplikacja jest skonfigurowana do używania odtwarzanie procesów i składniki są uruchomione w procesie obsługiwane COM +, nie można uruchomić usługi. To wymaganie nie obejmuje usług przy użyciu trybu w trakcie hostowanych w sieci Web, ponieważ nie są stosowane ustawienia odtwarzania procesu.  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd integrowania z aplikacjami COM](../../../../docs/framework/wcf/feature-details/integrating-with-com-applications-overview.md)

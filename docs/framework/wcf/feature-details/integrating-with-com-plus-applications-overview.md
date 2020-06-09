---
title: Przegląd integrowania z aplikacjami COM+
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, COM+ integration
- WCF, COM+ integration
ms.assetid: e481e48f-7096-40eb-9f20-7f0098412941
ms.openlocfilehash: 57a1537e1bde1efcd3586d032efee063561efcca
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84586497"
---
# <a name="integrating-with-com-applications-overview"></a>Przegląd integrowania z aplikacjami COM+
Windows Communication Foundation (WCF) oferuje bogate środowisko do tworzenia aplikacji rozproszonych. Jeśli korzystasz już z logiki aplikacji opartej na składnikach hostowanej w modelu COM+, możesz użyć programu WCF do rozbudowania istniejącej logiki zamiast konieczności jej ponownego zapisywania. Typowym scenariuszem jest udostępnienie istniejącej logiki biznesowej usług modelu COM+ lub przedsiębiorstwa za pomocą usług sieci Web.  
  
 Gdy interfejs składnika modelu COM+ jest udostępniany jako usługa sieci Web, Specyfikacja i Umowa tych usług są określane przez automatyczne mapowanie, które jest wykonywane podczas inicjacji aplikacji. Na poniższej liście przedstawiono model koncepcyjny dla tego mapowania:  
  
- Jedna usługa jest definiowana dla każdej uwidocznionej klasy COM.  
  
- Kontrakt usługi jest wyprowadzany bezpośrednio z definicji interfejsu wybranego składnika z możliwością wykluczenia metody zdefiniowanej w konfiguracji.  
  
- Operacje w tym kontrakcie są wyprowadzane bezpośrednio z metod w definicji interfejsu składnika.  
  
- Parametry dla tych operacji są wyprowadzane bezpośrednio z typu współdziałania COM, który odnosi się do parametrów metody składnika.  
  
 Domyślne adresy i powiązania transportu dla usługi są podane w pliku konfiguracji usługi, ale można je zmienić w razie potrzeby.  
  
> [!NOTE]
> Umowy dotyczące uwidocznionych usług sieci Web pozostają stałe, o ile interfejsy i konfiguracje modelu COM+ pozostaną bez zmian. Modyfikacja kilku interfejsów nie powoduje automatycznej aktualizacji dostępnych usług i wymaga ponownego uruchomienia narzędzia konfiguracji modelu usług modelu COM+ (ComSvcConfig. exe).  
  
 Wymagania dotyczące uwierzytelniania i autoryzacji aplikacji modelu COM+ i jej składników nadal są wymuszane, gdy są używane jako usługa sieci Web.  
  
 Jeśli obiekt wywołujący inicjuje transakcję usługi sieci Web, składniki oznaczone jako Rejestracja transakcyjna w ramach tego zakresu transakcji.  
  
 Poniższe kroki są wymagane do udostępnienia interfejsu składnika modelu COM+ jako usługi sieci Web bez modyfikowania składnika:  
  
1. Ustal, czy interfejs składnika modelu COM+ może być ujawniony jako usługa sieci Web.  
  
2. Wybierz odpowiedni tryb hostingu.  
  
3. Użyj narzędzia konfiguracji modelu usług modelu COM+ (ComSvcConfig. exe), aby dodać usługę sieci Web dla interfejsu. Aby uzyskać więcej informacji o sposobach korzystania z programu ComSvcConfig. exe, zobacz [How to: use a com+ Service Model Configuration Tool](how-to-use-the-com-service-model-configuration-tool.md).  
  
4. Skonfiguruj dodatkowe ustawienia usługi w pliku konfiguracji aplikacji. Aby uzyskać więcej informacji o konfigurowaniu składnika, zobacz [How to: Configure com Settings Service](how-to-configure-com-service-settings.md).  
  
## <a name="supported-interfaces"></a>Obsługiwane interfejsy  
 Istnieją pewne ograniczenia dotyczące typu interfejsów, które mogą być udostępniane jako usługa sieci Web. Następujące typy interfejsów nie są obsługiwane:  
  
- Interfejsy, które przekazują odwołania do obiektów jako parametry — opisane poniżej ograniczone podejście do odwołania do obiektu jest opisana w sekcji Obsługa odwołań do obiektów ograniczonych.  
  
- Interfejsy, które przechodzą typy, które nie są zgodne z .NET Framework konwersji współdziałania COM.  
  
- Interfejsy dla aplikacji, które mają włączone buforowanie aplikacji, gdy są hostowane przez model COM+.  
  
- Interfejsy składników, które są oznaczone jako prywatne dla aplikacji.  
  
- Interfejsy infrastruktury modelu COM+.  
  
- Interfejsy z aplikacji systemowej.  
  
- Interfejsy ze składników usług przedsiębiorstwa, które nie zostały dodane do globalnej pamięci podręcznej zestawów.  
  
### <a name="limited-object-reference-support"></a>Obsługa odwołań do ograniczonego obiektu  
 Ze względu na to, że wiele wdrożonych składników modelu COM+ używa obiektów według parametrów odwołań, takich jak zwracanie obiektu zestawu rekordów ADO, integracja modelu COM+ obejmuje ograniczoną obsługę parametrów odwołań do obiektów. Obsługa jest ograniczona do obiektów, które implementują `IPersistStream` interfejs com. Obejmuje to obiekty zestawu rekordów ADO i można zaimplementować dla obiektów COM specyficznych dla aplikacji.  
  
 Aby włączyć tę obsługę, narzędzie ComSvcConfig. exe udostępnia przełącznik **allowreferences** , który wyłącza parametr sygnatury metody regularnej i sprawdza, czy narzędzie jest uruchamiane, aby upewnić się, że parametry odwołania do obiektu nie są używane. Ponadto typy obiektów, które są przekazywane jako parametry, muszą być nazwane i identyfikowane w `persistableTypes` elemencie konfiguracji> <, który jest elementem podrzędnym elementu <`comContract`>.  
  
 Gdy ta funkcja jest używana, usługa integracji modelu COM+ używa `IPersistStream` interfejsu do serializacji lub deserializacji wystąpienia obiektu. Jeśli wystąpienie obiektu nie obsługuje `IPersistStream` , zgłaszany jest wyjątek.  
  
 W aplikacji klienckiej metody na <xref:System.ServiceModel.ComIntegration.PersistStreamTypeWrapper> obiekcie mogą służyć do przekazywania obiektu w usłudze i w sposób podobny do pobierania obiektu.  
  
> [!NOTE]
> Ze względu na niestandardową i specyficzną dla platformy sposób podejścia serializacji najlepiej jest to rozwiązanie do użycia między klientami programu WCF i usługami WCF.  
  
## <a name="selecting-the-hosting-mode"></a>Wybieranie trybu hostingu  
 Model COM+ uwidacznia usługi sieci Web w jednym z następujących trybów hostingu:  
  
- Obsługiwane przez model COM+  
  
     Usługa sieci Web jest hostowana w ramach dedykowanego procesu serwera COM+ aplikacji (dllhost. exe). Ten tryb wymaga, aby aplikacja była jawnie uruchamiana, zanim będzie mogła odbierać żądania usługi sieci Web. Opcje modelu COM+ "Uruchom jako usługa NT" lub "Pozostaw działające w trybie bezczynności" mogą służyć do zapobiegania bezczynnemu zamknięciu aplikacji i jej usług. Ten tryb zapewnia dostęp usługi sieci Web i modelu DCOM do aplikacji serwera.  
  
- Hostowane w sieci Web  
  
     Usługa sieci Web jest hostowana w procesie roboczym serwera sieci Web. Ten tryb nie wymaga aktywności modelu COM+ po odebraniu początkowego żądania. Jeśli aplikacja nie jest aktywna po odebraniu tego żądania, zostanie ona automatycznie aktywowana przed przetworzeniem żądania. Ten tryb zapewnia także dostęp usługi sieci Web i modelu DCOM do aplikacji serwera, ale powoduje przeskok procesu do żądań usług sieci Web. Zwykle wymaga to włączenia personifikacji przez klienta. W programie WCF można to zrobić z <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> właściwością <xref:System.ServiceModel.Security.WindowsClientCredential> klasy, do której uzyskuje się dostęp jako właściwość klasy generycznej <xref:System.ServiceModel.ChannelFactory%601> , a także <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation> wartości wyliczenia.  
  
- W procesie hostowanym w sieci Web  
  
     Usługa sieci Web i logika aplikacji modelu COM+ są hostowane w procesie roboczym serwera sieci Web. Zapewnia to automatyczną aktywację trybu hostowanego w sieci Web bez powodowania przeskoków procesów dla żądań usług sieci Web. Wadą jest to, że nie można uzyskać dostępu do aplikacji serwera za pomocą modelu DCOM.  
  
### <a name="security-considerations"></a>Zagadnienia związane z zabezpieczeniami  
 Podobnie jak w przypadku innych usług WCF, ustawienia zabezpieczeń dla uwidocznionej usługi są zarządzane za pomocą ustawień konfiguracji kanału WCF. Tradycyjne ustawienia zabezpieczeń DCOM, takie jak ustawienia uprawnień na poziomie komputera DCOM nie są wymuszane. Aby wymusić role aplikacji modelu COM+, należy włączyć autoryzację "sprawdzanie dostępu na poziomie składnika" dla składnika.  
  
 Użycie niezabezpieczonego powiązania może pozostawiać komunikację otwartą przed naruszeniem lub ujawnieniem informacji. Aby tego uniknąć, zalecamy użycie bezpiecznego powiązania.  
  
 W przypadku trybów hostowanych przez model COM+ i sieci Web aplikacje klienckie muszą zezwalać procesowi serwera na personifikowanie użytkownika klienta. Można to zrobić na klientach programu WCF, ustawiając poziom personifikacji na <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation> .  
  
 W przypadku usług Internet Information Services (IIS) lub Windows Process Activation Service (WAS) przy użyciu transportu HTTP narzędzie Httpcfg. exe może służyć do rezerwowania adresu punktu końcowego transportu. W innych konfiguracjach ważne jest ochronę przed nieautoryzowanymi usługami, które działają jako zamierzona usługa. Aby zapobiec uruchamianiu nieautoryzowanej usługi w żądanym punkcie końcowym, można skonfigurować legalną usługę do uruchamiania jako usługa NT. Dzięki temu uprawniony usługa może przejąć adres punktu końcowego przed wszelkimi nieautoryzowanymi usługami.  
  
 Podczas udostępniania aplikacji modelu COM+ ze skonfigurowanymi rolami modelu COM+ jako usługą hostowaną w sieci Web należy dodać do jednej z ról aplikacji opcję "Uruchom konto procesu IIS". To konto, zazwyczaj o nazwie IWAM_machinename, musi zostać dodane, aby można było włączyć czyste zamknięcie obiektów po użyciu. Kontu nie należy przyznawać żadnych dodatkowych uprawnień.  
  
 Funkcji odtwarzania procesów COM+ nie można używać w aplikacjach zintegrowanych. Jeśli aplikacja jest skonfigurowana do korzystania z odtwarzania procesów, a składniki są uruchomione w procesie hostowanym przez model COM+, uruchomienie usługi nie powiedzie się. To wymaganie nie obejmuje usług korzystających z trybu online hostowanych w sieci Web, ponieważ nie są stosowane ustawienia odtwarzania procesów.  
  
## <a name="see-also"></a>Zobacz też

- [Omówienie integracji z aplikacjami COM](integrating-with-com-applications-overview.md)

---
title: Testowy klient WCF (WcfTestClient.exe)
ms.date: 03/30/2017
ms.assetid: d4302855-677f-4640-aa90-c5d785d72fb7
ms.openlocfilehash: 56074bf051478e9da1bc11479284883f7321bd63
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916797"
---
# <a name="wcf-test-client-wcftestclientexe"></a>Testowy klient WCF (WcfTestClient.exe)
Windows Communication Foundation (WCF) Test Client (WcfTestClient. exe) to narzędzie graficznego interfejsu użytkownika, które umożliwia użytkownikom wprowadzanie parametrów testowych, przesyłanie tych danych do usługi i wyświetlanie odpowiedzi, którą usługa wysyła z powrotem. Zapewnia bezproblemowe środowisko testowania usług w połączeniu z hostem usługi WCF.  
  
 Zazwyczaj można znaleźć klienta testowego WCF (WcfTestClient. exe) w następującej lokalizacji: `C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\Common7\IDE` — społeczność może być jednym z "Enterprise", "Professional" lub "Community" w zależności od tego, jaki poziom programu Visual Studio jest zainstalowany.
  
## <a name="scenarios-for-using-test-client"></a>Scenariusze korzystania z klienta testowego  
 W poniższych sekcjach omówiono najczęstsze scenariusze, w których można użyć klienta testowego WCF w celu usprawnienia procesu tworzenia oprogramowania.  
  
### <a name="inside-visual-studio"></a>W programie Visual Studio  
  
#### <a name="wcf-service-host-starts-wcf-test-client-with-a-single-service"></a>Host usługi WCF uruchamia klienta testowego WCF przy użyciu jednej usługi  
 Po utworzeniu nowego projektu usługi WCF i naciśnięciu klawisza F5 w celu uruchomienia debugera, Host usługi WCF rozpocznie Hostowanie usługi w projekcie. Następnie zostanie otwarty klient testu WCF i zostanie wyświetlona lista punktów końcowych usługi zdefiniowanych w pliku konfiguracji. Możesz przetestować parametry i wywołać usługę i powtórzyć ten proces w celu ciągłego testowania i weryfikowania usługi.  
  
#### <a name="wcf-service-host-starts-wcf-test-client-with-multiple-services"></a>Host usługi WCF uruchamia klienta testowego WCF z wieloma usługami  
 Można również użyć klienta testowego WCF do ułatwienia debugowania projektu usługi, który zawiera wiele usług. Gdy klient testowy WCF zostanie otwarty, automatycznie iteruje listę usług w projekcie i otwiera je do testowania.  
  
### <a name="outside-visual-studio"></a>Poza programem Visual Studio  
 Możesz również wywołać klienta testowego WCF (WcfTestClient. exe) poza programem Visual Studio, aby przetestować dowolną usługę w Internecie. Aby zlokalizować narzędzie, przejdź do następującej lokalizacji:  
  
 `C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\Common7\IDE`(w przypadku, gdy społeczność może być jednym z "Enterprise", "Professional" lub "Community") w zależności od tego, jaki poziom programu Visual Studio jest zainstalowany na komputerze)
  
 Aby użyć narzędzia, kliknij dwukrotnie nazwę pliku, aby otworzyć ją z tej lokalizacji, lub uruchom ją z wiersza polecenia.  
  
 Klient testowy WCF przyjmuje dowolną liczbę identyfikatorów URI jako argumenty wiersza polecenia.  Są to identyfikatory URI usług, które mogą być testowane.  
  
 `wcfTestClient.exe URI1 URI2 …`  
  
 Po otwarciu okna klienta testowego WCF kliknij pozycję **plik**->**Dodaj usługę**, a następnie wprowadź adres punktu końcowego usługi, którą chcesz otworzyć.  
  
## <a name="wcf-test-client-user-interface"></a>Interfejs użytkownika klienta testowego WCF  
 Klienta testowego WCF można użyć z jedną usługą lub wieloma usługami.  
  
### <a name="service-operations"></a>Operacje usługi  
 W lewym okienku okna głównego klienta testowego programu WCF znajduje się lista wszystkich dostępnych usług wraz z ich punktami końcowymi i operacjami.  
  
 Po dwukrotnym kliknięciu operacji można wyświetlić jej zawartość w prawym okienku wewnątrz nowej karty z nazwą operacji.  
  
 Okienko po lewej stronie zawiera również listę plików konfiguracji klienta. Kliknij dwukrotnie dowolny element, aby wyświetlić zawartość pliku w nowym oknie z kartami w okienku po prawej stronie.  
  
### <a name="entering-test-parameters"></a>Wprowadzanie parametrów testu  
 Aby wyświetlić parametry testu, kliknij dwukrotnie operację, aby otworzyć ją w okienku po prawej stronie. Parametry są domyślnie wyświetlane w **formacie sformatowanym** i można wprowadzić dowolne wartości parametrów w celu przetestowania usługi.  
  
 Aby wyświetlić plik XML wiadomości, kliknij przycisk **XML**. Aby wysłać je do usługi, kliknij pozycję **Wywołaj**.  
  
 Dla parametru DataSet kliknij **...** przycisk obok pozycji **Edytuj...** Aby edytować go w nowym oknie zawierającym DataGrid. Zwróć uwagę na wygląd przycisków **Kopiuj zestaw danych** i **Wklej zestaw danych** . Jeśli schemat obiektu DataSet jest nieznany przy pierwszej edycji, element DataGrid jest pusty. Musisz wkleić obiekt DataSet z tym samym schematem do bieżącego obiektu w elemencie DataGrid. (Należy zauważyć, że przed operacją wklejenia należy skopiować schemat z innej lokalizacji). Możesz również skopiować obiekt DataSet do użycia w przyszłości, klikając przycisk **Kopiuj zestaw danych** .  
  
 Odpowiedź usługi jest wyświetlana poniżej parametrów testu.  
  
> [!NOTE]
> Jeśli oczekiwana wartość zwracana jest ciągiem, wynik będzie wyświetlany jako ciąg ujęty w cudzysłów, mimo że podane dane wejściowe nie są ujęte w cudzysłów.  
  
 Jeśli określono konkretną operację jako jednokierunkową podczas tworzenia kontraktu dla usługi, nie zostanie wyświetlona żadna odpowiedź usługi. Gdy tylko wiadomość zostanie umieszczona w kolejce do dostarczenia, pojawi się okno dialogowe z informacją o tym, że wiadomość została pomyślnie wysłana.  
  
### <a name="session-support"></a>Obsługa sesji  
 Pole wyboru **Uruchom nowy serwer proxy** na karcie operacji usługi umożliwia przełączenie obsługi sesji. To pole jest domyślnie wyczyszczone.  
  
 Po wprowadzeniu parametrów testu dla określonej operacji (lub innej operacji w tym samym punkcie końcowym usługi) i kliknięciu opcji Wywołaj wiele razy, gdy pole wyboru jest wyczyszczone, te operacje współużytkują jeden serwer proxy i stan usługi są utrwalane w wielu składowa.  
  
 Jeśli zaznaczone jest pole wyboru **Uruchom nowy serwer proxy** , zostanie uruchomiony nowy serwer proxy dla każdego **wywołania**, zostanie zakończony poprzedni scenariusz sesji i stan usługi zostanie zresetowany.  
  
### <a name="editing-client-configuration"></a>Edytowanie konfiguracji klienta  
 W lewym okienku okna głównego klienta testowego programu WCF wyświetlane są pliki konfiguracji klienta. Kliknij dwukrotnie dowolny element, aby wyświetlić zawartość pliku w okienku po prawej stronie.  
  
#### <a name="edit-with-service-configuration-editor"></a>Edytuj przy użyciu edytora konfiguracji usługi  
 W lewym okienku kliknij prawym przyciskiem myszy **plik konfiguracyjny** i wybierz menu kontekstowe **Edytuj za pomocą SvcConfigEditor**. Edytor konfiguracji usługi jest uruchamiany z zawartością konfiguracji klienta. Konfigurację można edytować i zapisać w narzędziu.  
  
 Po zapisaniu pliku w Edytorze konfiguracji usługi Klient testowy programu WCF wyświetli komunikat ostrzegawczy informujący o tym, że plik został zmodyfikowany poza programem i pyta, czy chcesz go załadować ponownie.  
  
 W przypadku wybrania **opcji tak**zawartość konfiguracji na karcie "Client. dll. config" odzwierciedla zmiany wprowadzone w edytorze.  
  
 W przypadku wybrania opcji **nie**zawartość konfiguracji na karcie "Client. dll. config" pozostaje niezmieniona, a zmodyfikowana zawartość jest automatycznie zapisywana w pliku źródłowym.  
  
#### <a name="restore-to-default-configuration"></a>Przywróć konfigurację domyślną  
 Jeśli chcesz anulować wszystkie zmiany i przywrócić domyślną konfigurację klienta, kliknij prawym przyciskiem myszy **plik konfiguracyjny** w okienku po lewej stronie i wybierz menu kontekstowe **Przywróć domyślną konfigurację**. Domyślna wartość konfiguracji została załadowana i zostanie przywrócona zawartość z karty "Client. dll. config".  
  
#### <a name="validate-changes"></a>Weryfikuj zmiany  
 Gdy zapisane zmiany są ładowane w kliencie testowym WCF, konfiguracja jest sprawdzana pod kątem poprawności względem schematu WCF. Jeśli zostaną znalezione błędy, wyświetlane jest okno dialogowe, aby wyświetlić szczegóły błędu.  
  
 Podczas generowania serwera proxy, kompilowania danych binarnych lub wywoływania usługi elementy menu, które obsługują edycję (czyli "Edytuj...", "Restore..." itd.), są wyłączone. Wywołanie usługi jest również wyłączone podczas ładowania zaktualizowanej konfiguracji do klienta testowego WCF.  
  
#### <a name="persist-client-configuration"></a>Utrwalanie konfiguracji klienta  
 Opcja **Narzędzia**->**Opcje** konfiguracji klienta zawiera pozycję zawsze Generuj ponownie konfigurację podczas uruchamiania usług, która jest domyślnie włączona.-> Ta opcja określa, że za każdym razem, gdy klient testu WCF ładuje usługę, generuje plik konfiguracji na podstawie najnowszego kontraktu usługi i plików App. config.  
  
 Jeśli edytowano konfigurację klienta usługi WCF i chcesz, aby zawsze używała tego zaktualizowanego pliku do debugowania usługi, można usunąć zaznaczenie opcji Regenerate. Dzięki temu nawet w przypadku aktualizowania usługi i ponownego otwarcia klienta testowego WCF, plik Client. dll. config jest tym, który wcześniej był aktualizowany, zamiast wygenerowanej ponownie na podstawie zaktualizowanej usługi.  
  
 Jednak może być konieczne edytowanie pliku konfiguracji, aby był on spójny z ponownie wygenerowanym serwerem proxy. Jeśli ponownie wygenerowany plik proxy i konfiguracyjny są niezgodne ze względu na zaktualizowaną usługę, błędy wystąpią, gdy usługa zostanie wywołana.  
  
> [!CAUTION]
>  Jeśli zmodyfikowano plik konfiguracji klienta i wybierzesz go ponownie w przyszłości, można znaleźć plik w następującej lokalizacji:  
>   
>  \Dokumenty i ustawienia\\[konto użytkownika] \Moje Documents\Test projekty klientów.  
>   
>  Wszystkie zaktualizowane informacje o poświadczeniach przechowywanych w pliku konfiguracji klienta są chronione przez listę Access Control (ACL) tego folderu.  
  
### <a name="adding-removing-and-refreshing-services"></a>Dodawanie, usuwanie i odświeżanie usług  
  
#### <a name="add-service"></a>Dodaj usługę  
 Kliknij pozycję **plik**->**Dodaj usługę** , aby dodać usługę do klienta testowego WCF. Następnie wymagane jest wpisanie identyfikatora URI (adresu punktu końcowego) usługi, która ma zostać dodana. Adres usługi może być adresem w formacie MEX lub WSDL.  
  
 Możesz również znaleźć listę 10 ostatnio dodanych punktów końcowych usługi w podmenu **ostatnich usług** . W przypadku wybrania jednego z nich określona usługa zostanie dodana do klienta testowego WCF.  
  
 Możesz również kliknąć prawym przyciskiem myszy element główny drzewa usług **Moje projekty usługi**, a następnie wybrać pozycję **Dodaj usługę** , aby osiągnąć ten sam wynik.  
  
 Podczas generowania serwera proxy, kompilowania danych binarnych lub wywołania usługi, elementy menu obsługujące Dodawanie usługi są wyłączone. Wywołanie usługi również jest wyłączone.  
  
#### <a name="remove-service"></a>Usuń usługę  
 Kliknij prawym przyciskiem myszy katalog główny usługi, który ma zostać usunięty, a następnie wybierz pozycję **Usuń usługę** , aby usunąć usługę z klienta testowego WCF.  
  
 Podczas generowania serwera proxy, kompilowania danych binarnych lub wywołania usługi elementy menu, które obsługują usuwanie usługi, są wyłączone. Wywołanie usługi również jest wyłączone.  
  
#### <a name="refresh-service"></a>Odśwież usługę  
 Jeśli w trakcie działania klienta testowego WCF została wprowadzona zmiana, a chcesz mieć pewność, że implementacja klienta testowego WCF dla tej usługi jest aktualna, kliknij prawym przyciskiem myszy katalog główny usługi, a następnie wybierz pozycję **Odśwież usługę**. Należy pamiętać, że po odświeżeniu stan usługi zostanie zresetowany.  
  
 Podczas generowania serwera proxy, kompilowania danych binarnych lub wywołania usługi, elementy menu, które obsługują odświeżanie usługi, są wyłączone. Wywołanie usługi również jest wyłączone.  
  
## <a name="location-of-files-generated-by-the-test-client"></a>Lokalizacja plików wygenerowanych przez klienta testowego  
 Domyślnie klient testowy WCF przechowuje wygenerowany kod klienta i pliki konfiguracji w folderze "%appdata%\Local\temp\Test Client projects". Ten folder jest usuwany po zakończeniu działania klienta testowego WCF. Jeśli plik konfiguracji jest modyfikowany w kliencie testowym WCF i opcja **zawsze Generuj ponownie konfigurację podczas uruchamiania usług** jest wyłączona, zmodyfikowany plik jest kopiowany do folderu "CachedConfig" w obszarze "Moje Documents\Test projekty klienta" z mapowaniem ( plik XML z metadanymi-Address-to-File-Name) jako indeks.  
  
 Możesz również uruchomić klienta testowego WCF w wierszu polecenia, użyj `/ProjectPath` przełącznika, aby określić nową ścieżkę do przechowywania wygenerowanych plików, lub `/RestoreProjectPath` Użyj przełącznika, aby przywrócić domyślną lokalizację. Składnia jest następująca:  
  
 `wcfTestClient.exe /ProjectPath [desired location]`  
  
 Uruchomienie tego polecenia nie powoduje otwarcia klienta testowego WCF. Zmieniono tylko lokalizację folderu. Można uruchomić to polecenie niezależnie od tego, czy klient testowy WCF jest uruchomiony. Nowa lokalizacja jest stosowana po ponownym uruchomieniu klienta testowego WCF. Informacje o lokalizacji można zapisać w rejestrze lub w pliku WcfTestClient. exe. Option w folderze "%appdata%\Local\temp\Test Client projects".  
  
## <a name="features-supported-by-wcf-test-client"></a>Funkcje obsługiwane przez klienta testowego WCF  
 Poniżej znajduje się lista funkcji obsługiwanych przez klienta testowego WCF:  
  
- Wywołanie usługi: Komunikat z żądaniem/odpowiedzi i jednokierunkową.  
  
- Powiązania: wszystkie powiązania obsługiwane przez Svcutil. exe.  
  
- Sterowanie sesją.  
  
- Kontrakt wiadomości.  
  
- Serializacji XML.  
  
 Poniżej znajduje się lista funkcji nieobsługiwanych przez klienta testowego WCF:  
  
- Typy: <xref:System.IO.Stream>, <xref:System.ServiceModel.Channels.Message>, <xref:System.Xml.XmlElement> <xref:System.Xml.Linq.XElement> ,,,typy<xref:System.Xml.Serialization.XmlSchemaProviderAttribute> implementujące <xref:System.Xml.Serialization.IXmlSerializable> interfejs, łącznie z atrybutem pokrewnym i typy i <xref:System.Xml.Linq.XDocument> <xref:System.Xml.XmlAttribute> <xref:System.Xml.XmlNode> i typ ADO.NET <xref:System.Data.DataTable> .  
  
- Kontrakt dupleksowy.  
  
- Transaction.  
  
- Bezpieczeństw CardSpace, certyfikat i nazwa użytkownika/hasło.  
  
- Powiązań WSFederationbinding, wszystkie powiązania kontekstu i powiązania https, WebHttpBinding (obsługa komunikatów odpowiedzi JSON).  
  
## <a name="closing-wcf-test-client"></a>Zamykanie klienta testowego WCF  
 Klienta testowego WCF można zamknąć w następujący sposób:  
  
- W menu **plik** kliknij polecenie **Zakończ**. Alternatywnie, w oknie głównym klienta testowego WCF kliknij przycisk **Zamknij**. Obie te akcje również zamykają funkcję Autohost usługi WCF i zatrzymają proces debugowania programu Visual Studio, jeśli klient testowy WCF został uruchomiony przez program Visual Studio.  
  
- Kliknij prawym przyciskiem myszy ikonę **hosta usługi WCF** w obszarze powiadomień, a następnie kliknij przycisk **Zakończ.** Spowoduje to zamknięcie funkcji autohostu usługi WCF i klienta testowego WCF i zatrzymanie procesu debugowania programu Visual Studio.  
  
## <a name="see-also"></a>Zobacz także

- [Host usługi WCF (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)

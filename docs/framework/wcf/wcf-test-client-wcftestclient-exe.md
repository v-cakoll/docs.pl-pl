---
title: Testowy klient WCF (WcfTestClient.exe)
ms.date: 03/30/2017
ms.assetid: d4302855-677f-4640-aa90-c5d785d72fb7
ms.openlocfilehash: 4e3531b91382c4d47aed73198bd8dd954ae4ca1f
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50181595"
---
# <a name="wcf-test-client-wcftestclientexe"></a>Testowy klient WCF (WcfTestClient.exe)
Windows Communication Foundation (WCF) testowanie klient (WcfTestClient.exe) jest narzędziem graficznego interfejsu użytkownika, które umożliwia użytkownikom testu parametrów wejściowych, przesyłanie, że dane wejściowe do usługi i wyświetlanie odpowiedzi, który usługa wysyła z powrotem. Zapewnia bezproblemowe usługi testowania doświadczenie w połączeniu z hosta usługi WCF.  
  
 Testowy klient WCF (WcfTestClient.exe) można zwykle znaleźć w następującej lokalizacji: `C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\Common7\IDE` — społeczności może być jedną z "Enterprise", "Professional" lub "Społeczność" w zależności od poziomu, który program Visual Studio jest zainstalowany.
  
## <a name="scenarios-for-using-test-client"></a>Scenariusze dotyczące korzystania z klienta testowego  
 W poniższych sekcjach omówiono najbardziej typowych scenariuszy, w których można użyć klienta testowego WCF w celu uproszczenia procesu opracowywania.  
  
### <a name="inside-visual-studio"></a>W programie Visual Studio  
  
#### <a name="wcf-service-host-starts-wcf-test-client-with-a-single-service"></a>Usługa hosta uruchamia WCF klienta testowego WCF z jedną usługą  
 Po utworzeniu nowego projektu usługi WCF i naciśnij klawisz F5, aby uruchomić debuger, Host usługi WCF rozpoczyna się do obsługi usługi w projekcie. Następnie klient testowy WCF otwiera i wyświetla listę punktów końcowych usługi zdefiniowane w pliku konfiguracyjnym. Można przetestować parametrów i wywołać usługę i powtórz ten proces nieprzerwanie testować i weryfikować usługi.  
  
#### <a name="wcf-service-host-starts-wcf-test-client-with-multiple-services"></a>Usługa hosta uruchamia WCF klienta testowego WCF z wieloma usługami  
 Testowy klient WCF umożliwia również debugować projekt usługi, który zawiera wiele usług. Po otwarciu klienta testowego WCF automatycznie wykonuje iterację na liście usług w swoim projekcie i otwiera je do testowania.  
  
### <a name="outside-visual-studio"></a>Poza programem Visual Studio  
 Testowanie klienta WCF (WcfTestClient.exe) można także wywoływać poza programem Visual Studio, aby przetestować dowolnych usług w Internecie. Aby zlokalizować narzędziu, przejdź do następującej lokalizacji:  
  
 `C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\Common7\IDE` (których społeczność może być "Enterprise", "Professional" lub "Społeczność" zależności od poziomu programu Visual Studio jest zainstalowany na komputerze)
  
 Aby użyć narzędzia, kliknij dwukrotnie nazwę pliku, aby otworzyć go w tej lokalizacji lub uruchomić go z wiersza polecenia.  
  
 Testowy klient WCF przyjmuje dowolną liczbę identyfikatorów URI jako argumenty wiersza polecenia.  Są to identyfikatory URI usług, które mogą być testowane.  
  
 `wcfTestClient.exe URI1 URI2 …`  
  
 Po otwarciu okna klienta testowego WCF, kliknij przycisk **pliku**->**Dodaj usługę**, a następnie wprowadź adres punktu końcowego usługi, który chcesz otworzyć.  
  
## <a name="wcf-test-client-user-interface"></a>Interfejs użytkownika klienta testowego WCF  
 Za pomocą klienta testowego WCF przy użyciu jednej usługi lub wielu usług.  
  
### <a name="service-operations"></a>Operacje usługi  
 Okienka po lewej stronie okna głównego klienta testowego WCF zawiera listę wszystkich dostępnych usług, oraz ich odpowiednich punktów końcowych i operacji.  
  
 Po dwukrotnym kliknięciu operacji można wyświetlić jego zawartość, w okienku po prawej stronie w nowej karcie operacji o nazwie.  
  
 W okienku po lewej stronie zawiera również listę plików konfiguracji klienta. Kliknij dwukrotnie dowolny z elementów, aby wyświetlić zawartość pliku w nowym oknie z kartami w okienku po prawej stronie.  
  
### <a name="entering-test-parameters"></a>Wprowadzanie parametrów testu  
 Aby wyświetlić parametry testu, kliknij dwukrotnie działanie, aby otworzyć go w okienku po prawej stronie. Parametry są wykazało, że w **sformatowany** widoku domyślnie, i możesz wprowadzić dowolne wartości parametrów przetestować usługę.  
  
 Aby wyświetlić komunikatu XML, kliknij **XML**. Aby wysłać je do usługi, kliknij przycisk **Invoke**.  
  
 Dla parametru zestawu danych, kliknij przycisk **...** przycisk Dalej, aby **Edytuj...** Aby edytować go w nowym oknie, wyświetlanie elementu DataGrid. Zwróć uwagę, wygląd **zestawu kopii danych** i **DataSet Wklej** przycisków. Jeśli schemat zestawu danych obiektu jest nieznany po pierwszym edycji, DataGrid jest pusty. Należy wkleić obiekt DataSet z ten sam schemat do bieżącego obiektu w elemencie DataGrid. (Zwróć uwagę, należy skopiować schematu z innym miejscu przed wykonaniem operacji wklejania). Można także skopiować obiekt zestawu danych do użycia w przyszłości, klikając **zestawu kopii danych** przycisku.  
  
 Odpowiedź usługi pojawia się poniżej parametrów testu.  
  
> [!NOTE]
>  Jeśli wartość zwracaną oczekiwany jest ciąg, wynik pojawi się jako ciąg w cudzysłowach, nawet jeśli nie dostarczono danych wejściowych w cudzysłowie.  
  
 Jeśli określonej operacji został określony jako jednokierunkowe, po utworzeniu kontraktu usługi, zostanie wyświetlony braku odpowiedzi usługi. Tak szybko, jak długo komunikat w kolejce do dostarczenia, okno dialogowe pojawia się powiadomienie, że wiadomość została wysłana pomyślnie.  
  
### <a name="session-support"></a>Obsługa sesji  
 **Uruchomić nowy serwer proxy** pole wyboru na karcie operacji usługi pozwala na przełączanie obsługę sesji. To pole jest domyślnie wyczyszczone.  
  
 Po wprowadź parametry testu dla określonej operacji (lub innej operacji w ten sam punkt końcowy usługi) i kliknięciu **Invoke** wiele razy, przy czym pole wyboru jest wyczyszczone, te operacje współkorzystają jeden serwer proxy i stan usługi utrwalane w wielu operacjach.  
  
 Jeśli **uruchomić nowy serwer proxy** pole wyboru jest zaznaczone, nowy serwer proxy rozpoczyna się dla każdego **Invoke**scenariusza poprzednia sesja zostanie zakończona i stan usługi zostanie zresetowana.  
  
### <a name="editing-client-configuration"></a>Edytowanie konfiguracji klienta  
 Okienka po lewej stronie okna głównego klienta testowego WCF zawiera listę plików konfiguracji klienta. Kliknij dwukrotnie dowolny z elementów, aby wyświetlić zawartość pliku w okienku po prawej stronie.  
  
#### <a name="edit-with-service-configuration-editor"></a>Edytuj za pomocą edytora konfiguracji usługi  
 Kliknij prawym przyciskiem myszy **pliku konfiguracyjnego** w okienku po lewej stronie i wybierz menu kontekstowe **edytować za pomocą narzędzia SvcConfigEditor**. Edytor konfiguracji usługi jest uruchamiany z zawartością konfiguracji klienta. Można edytować konfiguracji i zapisz go w narzędziu.  
  
 Po zapisaniu pliku w oknie edytora konfiguracji usługi, klient testowy WCF wyświetla komunikat ostrzegawczy z informacją, że plik został zmodyfikowany poza i pyta, czy chcesz załadować go ponownie.  
  
 Jeśli wybierzesz **tak**, zawartość konfiguracji na karcie "Plik Client.dll.config" odzwierciedla zmiany wprowadzone w edytorze.  
  
 Jeśli wybierzesz **nie**zawartość konfiguracji na karcie "Plik Client.dll.config" pozostaje niezmieniona i zmodyfikowanej zawartości są automatycznie zapisywane w pliku źródłowym.  
  
#### <a name="restore-to-default-configuration"></a>Przywróć domyślną konfigurację  
 Jeśli chcesz anulować wszystkie zmiany i przywrócić do domyślnej konfiguracji klienta, kliknij prawym przyciskiem myszy **pliku konfiguracyjnego** w okienku po lewej stronie i wybierz menu kontekstowe **Przywróć konfigurację domyślną**. Wartość domyślna konfiguracja zostanie załadowany, i zostanie przywrócona zawartość na karcie "Plik Client.dll.config".  
  
#### <a name="validate-changes"></a>Sprawdzenia poprawności zmian  
 Gdy zapisane zmiany są ładowane w kliencie testowym WCF, konfiguracji jest sprawdzane pod kątem poprawności względem schematu WCF. Jeśli wystąpią błędy, aby wyświetlić szczegóły błędu zostanie wyświetlone okno dialogowe.  
  
 Podczas generowania serwera proxy, kompilowanie binarne lub wywoływania usługi są wyłączone, elementy menu, które obsługują edytowanie (czyli "Edytuj...", "Przywracanie..." i tak dalej). Wywołania usługi jest niedostępne podczas ładowania aktualizowania konfiguracji do klienta testowego WCF.  
  
#### <a name="persist-client-configuration"></a>Utrwalanie konfiguracji klienta  
 **Narzędzia**->**opcje**->**konfiguracji klienta** karta zawiera **zawsze Generuj konfiguracji podczas uruchamiania Usługi** opcja, która jest domyślnie włączona. Ta opcja określa, że za każdym razem, gdy klient testowy WCF ładowania usługi generuje plik konfiguracji na podstawie najnowszych kontrakt usługi i pliki App.config usługi.  
  
 Jeśli edytowano konfiguracji klienta dla usługi WCF i chcesz zawsze używaj tego zaktualizowanego pliku do debugowania usługi, możesz usunąć zaznaczenie **ponownie wygenerować** opcji. Dzięki temu nawet wtedy, gdy aktualizacja usługi i otwórz ponownie klienta testowego WCF, plik plik Client.dll.config jest ten, który wcześniej zaktualizowano zamiast wygenerowano, jeden na podstawie zaktualizowane usługi.  
  
 Jednak może być konieczne edytowanie pliku konfiguracyjnego, aby uspójnić je przy użyciu wygenerowano serwera proxy. Jeśli wygenerowano serwera proxy i pliku konfiguracji są niezgodne z powodu usługi zaktualizowane, wystąpią błędy podczas wywoływania usługi.  
  
> [!CAUTION]
>  Jeśli zmodyfikowano plik konfiguracji klienta, a następnie wybierz, aby użyć go ponownie w przyszłości, można znaleźć pliku w następującej lokalizacji:  
>   
>  \Documents and Settings\\projektów klienckich \My Documents\Test [konto].  
>   
>  Wszelkie informacje zaktualizowanego poświadczenia przechowywane w pliku konfiguracji klienta jest chroniony przez listy kontroli dostępu (ACL) tego folderu.  
  
### <a name="adding-removing-and-refreshing-services"></a>Dodawanie, usuwanie i odświeżanie usługi  
  
#### <a name="add-service"></a>Dodaj usługę  
 Kliknij przycisk **pliku**->**Dodaj usługę** dodać usługę do klienta testowego WCF. Następnie należy wpisz identyfikator URI (adres punktu końcowego) usługi do dodania. Adres usługi może być adresem mex lub WSDL.  
  
 Możesz również znaleźć listę punktów końcowych z 10 ostatnio dodane usług w **ostatnio używane usługi** podmenu. Po wybraniu jednej z nich, określona usługa jest dodawany do klienta testowego WCF.  
  
 Również kliknięciu prawym przyciskiem myszy katalog główny w drzewie usług **Moje projekty usług**i wybierz **Dodaj usługę** aby osiągnąć ten sam wynik.  
  
 Podczas proxy generowania, kompilowania binarne lub wywołania usługi elementów menu, które obsługuje dodawanie usług telefonii są wyłączone. Wywołania usługi jest niedostępne.  
  
#### <a name="remove-service"></a>Usuń usługę  
 Kliknij prawym przyciskiem myszy element główny usługi usługi do usunięcia, a następnie wybierz pozycję **Usuń usługę** Aby usunąć usługę z klienta testowego WCF.  
  
 Podczas proxy generowania, kompilowania binarne lub wywołania usługi elementów menu, które obsługują usuwania usługi są wyłączone. Wywołania usługi jest niedostępne.  
  
#### <a name="refresh-service"></a>Usługa odświeżania  
 Zmianie z usługą podczas klienta testowego WCF jest uruchomiona, i chce mieć pewność, że implementacja klienta testowego WCF dla tej usługi jest aktualne, kliknij prawym przyciskiem myszy usługę, a następnie wybierz element główny usługi **odświeżania usługi**. Należy pamiętać, że po odświeżeniu stan usługi jest resetowany.  
  
 Podczas serwera proxy są wyłączone, elementy menu do generowania, kompilowania binarne lub wywołania usługi, które obsługuje odświeżania usługi. Wywołania usługi jest niedostępne.  
  
## <a name="location-of-files-generated-by-the-test-client"></a>Lokalizacja plików wygenerowanych przez klienta testowego  
 Domyślnie klient testowy WCF magazynów generowane klienta kod i pliki konfiguracyjne w folderze "%appdata%\Local\temp\Test projektów klienckich". Ten folder jest usuwany po zakończeniu klienta testowego WCF. Jeśli plik konfiguracji zostanie zmodyfikowany w kliencie testowym WCF i **zawsze Generuj konfiguracji podczas uruchamiania usługi** opcja jest wyłączona, zmodyfikowany plik zostanie skopiowany do folderu "Pamięci podręcznej konfiguracji" w obszarze "Moje Documents\Test projektów klienckich Projektów klienckich Documents\Test"za pomocą mapowania pliku XML (metadane adres pliku nazwa) jako indeks.  
  
 Można również uruchomić klienta testowego WCF w wierszu polecenia, użyj `/ProjectPath` przełączyć się do określenia nowej ścieżki odpowiednią do przechowywania plików wygenerowanych lub użyj `/RestoreProjectPath` przełącznika, aby przywrócić domyślną lokalizację. Składnia jest następująca:  
  
 `wcfTestClient.exe /ProjectPath [desired location]`  
  
 Uruchomienie tego polecenia nie zostanie otwarty klienta testowego WCF. Tylko lokalizacja folderu jest zmieniany. Czy klient testowy WCF jest uruchomiona lub nie można uruchomić tego polecenia. Nowa lokalizacja jest stosowana po ponownym uruchomieniu klienta testowego WCF. Informacje o lokalizacji można zapisać w rejestrze lub w pliku WcfTestClient.exe.option w folderze "%appdata%\Local\temp\Test projektów klienckich".  
  
## <a name="features-supported-by-wcf-test-client"></a>Funkcje obsługiwane przez klienta testowego WCF  
 Oto lista funkcji obsługiwanych przez klienta testowego WCF:  
  
-   Usługa wywołania: Żądanie/odpowiedź, a komunikat jednokierunkowy.  
  
-   Powiązania: obsługiwane przez Svcutil.exe wszystkie powiązania.  
  
-   Kontrolowanie sesji.  
  
-   Kontrakt komunikatu.  
  
-   Serializacji XML.  
  
 Oto lista funkcji nie są obsługiwane przez klienta testowego WCF:  
  
-   Typy: <xref:System.IO.Stream>, <xref:System.ServiceModel.Channels.Message>, <xref:System.Xml.XmlElement>, <xref:System.Xml.XmlAttribute>, <xref:System.Xml.XmlNode>, typami, które implementują <xref:System.Xml.Serialization.IXmlSerializable> interfejsu, w tym powiązane <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> atrybutu, a <xref:System.Xml.Linq.XDocument> i <xref:System.Xml.Linq.XElement> typów i ADO.NET <xref:System.Data.DataTable> typu.  
  
-   Kontraktu dwukierunkowego.  
  
-   Transakcja.  
  
-   Zabezpieczenia: [!INCLUDE[infocard](../../../includes/infocard-md.md)] , certyfikatów i nazwy użytkownika i hasła.  
  
-   Powiązania: WSFederationbinding, wszelkie kontekst powiązania i powiązanie Https, WebHttpbinding (Obsługa komunikatów w odpowiedzi Json).  
  
## <a name="closing-wcf-test-client"></a>Zamykanie klienta testowego WCF  
 Możesz zamknąć klienta testowego WCF w następujący sposób:  
  
-   Na **pliku** menu, kliknij przycisk **zakończenia**. Alternatywnie w oknie głównym klienta testowego WCF kliknij **Zamknij**. Z tych akcji również zamknąć hostów Auto usługi WCF i Zatrzymaj proces debugowania programu Visual Studio, jeśli klient testowy WCF została uruchomiona przez program Visual Studio.  
  
-   Kliknij prawym przyciskiem myszy **Host usługi WCF** ikonę w obszarze powiadomień, a następnie kliknij **zakończenia.** To jest zamykana z klienta testowego WCF i hostów Auto usługi WCF i zatrzymuje proces debugowania programu Visual Studio.  
  
## <a name="see-also"></a>Zobacz też  
 [Host usługi WCF (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)

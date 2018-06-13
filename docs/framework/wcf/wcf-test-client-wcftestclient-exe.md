---
title: Testowy klient WCF (WcfTestClient.exe)
ms.date: 03/30/2017
ms.assetid: d4302855-677f-4640-aa90-c5d785d72fb7
ms.openlocfilehash: 78be40268b46c4c85ee034db67d67ee0fbf2158f
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33809748"
---
# <a name="wcf-test-client-wcftestclientexe"></a>Testowy klient WCF (WcfTestClient.exe)
Windows Communication Foundation (WCF) testowanie klienta (WcfTestClient.exe) jest narzędzie graficznego interfejsu użytkownika, które użytkownicy mogą wprowadzić parametry testu, że dane wejściowe do usługi przesyłania i wyświetlić usługi odsyła odpowiedź. Zapewnia bezproblemowe usługi testowania czynności w połączeniu z hosta usługi WCF.  
  
 Klienta testowego WCF (WcfTestClient.exe) zwykle można znaleźć w następującej lokalizacji: C:\Program Files (x86) \Microsoft Visual Studio\2017\Community\Common7\IDE — społeczność może być "Przedsiębiorstwa", "Professional" lub "Społeczności", w zależności od której poziom programu Visual Studio jest zainstalowany.
  
## <a name="scenarios-for-using-test-client"></a>Scenariusze korzystania z klienta testowego  
 W poniższych sekcjach omówiono najbardziej typowych scenariuszy, w których można użyć klienta testowego WCF w celu uproszczenia procesu tworzenia.  
  
### <a name="inside-visual-studio"></a>W programie Visual Studio  
  
#### <a name="wcf-service-host-starts-wcf-test-client-with-a-single-service"></a>Usługa hosta uruchamia WCF klienta testowego WCF z jedną usługą  
 Po utworzeniu nowego projektu usługi WCF i naciśnij klawisz F5, aby uruchomić debugera, Host usługi WCF rozpoczyna się do obsługi usługi w projekcie. Następnie klienta testowego WCF otwiera i wyświetla listę punktów końcowych usługi zdefiniowane w pliku konfiguracyjnym. Można przetestować parametry i wywoływanie usługi i powtórz ten proces, aby stale testowanie i weryfikowanie usługi.  
  
#### <a name="wcf-service-host-starts-wcf-test-client-with-multiple-services"></a>Usługa hosta uruchamia WCF klienta testowego WCF z wieloma usługami  
 Umożliwia także klienta testowego WCF debugować projektu usługi, który zawiera wiele usług. Po otwarciu klienta testowego WCF automatycznie wykonuje iterację na liście usług w projekcie i otwiera je do testowania.  
  
### <a name="outside-visual-studio"></a>Poza programu Visual Studio  
 Testowanie klienta WCF (WcfTestClient.exe) można także wywoływać poza programem Visual Studio, aby przetestować dowolnych usług w Internecie. Aby zlokalizować narzędzia, przejdź do następującej lokalizacji:  
  
 C:\Program Files\Microsoft 9.0\Common7\IDE\ programu Visual Studio  
  
 Aby użyć narzędzia, kliknij dwukrotnie nazwę pliku, aby otworzyć go z tej lokalizacji lub uruchomić go z wiersza polecenia.  
  
 Klienta testowego WCF przyjmuje dowolnego liczba identyfikatorów URI jako argumenty wiersza polecenia.  Są to identyfikator URI usług, które można zbadać.  
  
 `wcfTestClient.exe URI1 URI2 …`  
  
 Po otwarciu okna klienta testowego WCF, kliknij przycisk **pliku**->**Dodaj usługę**, a następnie wprowadź adres punktu końcowego usługi, którą chcesz otworzyć.  
  
## <a name="wcf-test-client-user-interface"></a>Interfejs użytkownika klienta testowego WCF  
 Można użyć klienta testowego WCF z usługą jednego lub wielu usług.  
  
### <a name="service-operations"></a>Operacje usługi  
 W okienku po lewej stronie okna głównego klienta testowego WCF zawiera listę wszystkich dostępnych usług, oraz ich odpowiednich punktów końcowych i operacji.  
  
 Po dwukrotnym kliknięciu operacji, można wyświetlić jego zawartość w okienku po prawej stronie wewnątrz nową kartę o nazwie wykonać operację.  
  
 W okienku po lewej stronie zawiera także listę plików konfiguracji klienta. Kliknij dwukrotnie dowolny z elementów do wyświetlenia zawartości pliku w nowym oknie z kartami w okienku po prawej stronie.  
  
### <a name="entering-test-parameters"></a>Wprowadzanie parametrów testu  
 Aby wyświetlić parametry testu, kliknij dwukrotnie operację, aby otworzyć go w okienku po prawej stronie. Parametry są pokazanego **sformatowany** widoku domyślnie i będzie można wprowadzić dowolne wartości z parametrów przetestować usługę.  
  
 Aby wyświetlić wiadomości XML, kliknij przycisk **XML**. Aby wysłać je do usługi, kliknij przycisk **Invoke**.  
  
 Dla parametru zestawu danych, kliknij przycisk **...** przycisk Dalej, aby **edycji...** Aby edytować go w nowym oknie przedstawiający elementu DataGrid. Zwróć uwagę, wygląd **kopiowania zestawu danych** i **DataSet Wklej** przycisków. Jeśli schemat obiektu DataSet jest nieznany po pierwszym edycji, DataGrid jest pusta. Należy wkleić obiekt DataSet z tego samego schematu do bieżącego obiektu w elemencie DataGrid. (Zwróć uwagę, należy skopiować schematu w innym miejscu przed operacji wklejania). Można także skopiować obiekt zestawu danych do użycia w przyszłości, klikając **kopiowania zestawu danych** przycisku.  
  
 Odpowiedź usługi pojawia się poniżej parametry testu.  
  
> [!NOTE]
>  Jeśli oczekiwane zwracana wartość jest ciągiem, wynik zostanie wyświetlony jako ciągu w cudzysłowie nawet, jeśli określone dane wejściowe nie był w cudzysłowy.  
  
 Jeśli określone określonej operacji jako jednokierunkowe podczas tworzenia kontraktu usługi, wyświetlany jest brak odpowiedzi usługi. Jak wiadomość jest w kolejce w celu dostarczania, okno dialogowe wyskakującej informujący o tym, że wiadomość została wysłana pomyślnie.  
  
### <a name="session-support"></a>Obsługa sesji  
 **Uruchomić nowego serwera proxy** pole wyboru na karcie operacji usługi umożliwia przełączanie sesji pomocy technicznej. To pole jest domyślnie wyczyszczone.  
  
 Gdy wprowadź parametry testu dla określonej operacji (lub innej operacji w tym samym punktu końcowego usługi) i kliknij przycisk **Invoke** wielokrotnie wyczyszczone pole wyboru tych operacji udostępnianie jeden serwer proxy i jest stan usługi trwała dla wielu operacji.  
  
 Jeśli **uruchomić nowego serwera proxy** pole wyboru jest zaznaczone, uruchomieniu nowego serwera proxy dla każdego **Invoke**scenariusza poprzednia sesja zostanie zakończona i stan usługi zostanie zresetowana.  
  
### <a name="editing-client-configuration"></a>Edytowanie konfiguracji klienta  
 W okienku po lewej stronie okna głównego klienta testowego WCF zawiera listę plików konfiguracji klienta. Kliknij dwukrotnie dowolny z elementów do wyświetlenia zawartości pliku w okienku po prawej stronie.  
  
#### <a name="edit-with-service-configuration-editor"></a>Edytuj z edytora konfiguracji usługi  
 Kliknij prawym przyciskiem myszy **pliku konfiguracyjnego** w okienku po lewej stronie i wybierz menu kontekstowe **edytować za pomocą SvcConfigEditor**. Edytor konfiguracji usługi jest uruchamiana z zawartością konfiguracji klienta. Można edytować konfiguracji i zapisz go w narzędziu.  
  
 Po zapisaniu pliku w oknie edytora konfiguracji usługi, klienta testowego WCF wyświetla komunikat ostrzegawczy z informacją, że plik został zmodyfikowany poza i zapyta, czy chcesz załadować go ponownie.  
  
 W przypadku wybrania **tak**, zawartość konfiguracji na karcie "Plik Client.dll.config" odzwierciedla zmiany wprowadzone w edytorze.  
  
 W przypadku wybrania **nr**, zawartość konfiguracji na karcie "Plik Client.dll.config" pozostaje niezmieniona i zmodyfikowanej zawartości są automatycznie zapisywane w pliku źródłowym.  
  
#### <a name="restore-to-default-configuration"></a>Przywrócenie konfiguracji domyślnej  
 Jeśli chcesz anulować wszystkie zmiany i przywrócić domyślnej konfiguracji klienta, kliknij prawym przyciskiem myszy **pliku konfiguracyjnego** w okienku po lewej stronie i wybierz menu kontekstowe **Przywróć konfigurację domyślną**. Wartość domyślna konfiguracja zostanie załadowany i zawartości na karcie "Plik Client.dll.config" został przywrócony.  
  
#### <a name="validate-changes"></a>Sprawdzanie poprawności zmiany  
 Zapisano zmiany są ładowane w kliencie testowym WCF, konfiguracja jest sprawdzany pod kątem poprawności względem schematu WCF. Jeśli zostaną znalezione błędy, aby wyświetlić szczegóły błędu jest wyświetlone okno dialogowe.  
  
 Generowanie serwera proxy, binarnych kompilacji lub wywoływania usługi są wyłączone elementy menu, które obsługuje edycji (to znaczy "Edytuj...", "Przywracanie..." i tak dalej). Wywołania usługi jest niedostępne podczas ładowania aktualizacji konfiguracji do klienta testowego WCF.  
  
#### <a name="persist-client-configuration"></a>Utrwalanie konfiguracji klienta  
 **Narzędzia**->**opcje**->**konfiguracji klienta** karta zawiera **zawsze Generuj konfiguracji podczas uruchamiania Usługi** opcja, która jest domyślnie włączona. Ta opcja określa, że za każdym razem, gdy klienta testowego WCF ładuje usługi, generuje plik konfiguracji na podstawie najnowszych kontrakt usługi i pliki App.config usługi.  
  
 Jeśli edytowano konfiguracji klienta dla usługi WCF i chcesz zawsze używaj zaktualizowanego pliku do debugowania z usługą, możesz usunąć zaznaczenie pola **ponownie wygenerować** opcji. W ten sposób, nawet wtedy, gdy aktualizacja usługi i ponownie otwórz klienta testowego WCF, pliku plik Client.dll.config jest aktualizowany wcześniej zamiast wygenerowano ponownie, jeden na podstawie zaktualizowane usługi.  
  
 Jednak może być konieczne edycję pliku konfiguracyjnego, aby je dostosować za pomocą ponownie wygenerowanego serwera proxy. Jeśli ponownie wygenerowanego serwera proxy i pliku konfiguracji są niezgodne z powodu zaktualizowane usługi, błędy zostanie przeprowadzona po wywołaniu usługi.  
  
> [!CAUTION]
>  Jeśli zmodyfikowano plik konfiguracji klienta i wybrać opcję ponownego użycia w przyszłości, można znaleźć pliku w następującej lokalizacji:  
>   
>  \Documents and Settings\\projektów klienckich \My Documents\Test [konta użytkownika].  
>   
>  Żadnych informacji dotyczących zaktualizowanych poświadczeń przechowywanych w pliku konfiguracji klienta jest chroniony przez listy kontroli dostępu (ACL) tego folderu.  
  
### <a name="adding-removing-and-refreshing-services"></a>Dodawanie, usuwanie i odświeżanie usługi  
  
#### <a name="add-service"></a>Dodawanie usługi  
 Kliknij przycisk **pliku**->**Dodaj usługę** do dodawania usługi do klienta testowego WCF. Następnie należy wpisać identyfikator URI (adres punktu końcowego) usługi do dodania. Adres usługi może być adresem mex lub WSDL.  
  
 Możesz także znaleźć listę punktów końcowych 10 ostatnio dodane usług w **ostatnie usług** podmenu. Po wybraniu jednej z nich, określona usługa jest dodawany do klienta testowego WCF.  
  
 Użytkownik może również kliknij prawym przyciskiem myszy korzeń drzewa usługi **Moje projekty usług**i wybierz **Dodaj usługę** uzyskanie takiego samego wyniku.  
  
 Podczas proxy generowania, kompilowania binarnego lub wywołania usługi elementów menu, które obsługuje dodawania usługi są wyłączone. Wywołania usługi jest niedostępne.  
  
#### <a name="remove-service"></a>Usunięcie usługi  
 Kliknij prawym przyciskiem myszy element główny usługi usługi można usunąć, a następnie wybierz **Usuń usługi** do usunięcia usługi od klienta testowego WCF.  
  
 Podczas proxy generowania, kompilowania binarnego lub wywołania usługi elementów menu, które obsługuje usuwanie usługi są wyłączone. Wywołania usługi jest niedostępne.  
  
#### <a name="refresh-service"></a>Odśwież usługi  
 Zmianie do usługi podczas klienta testowego WCF jest uruchomiona, i chcesz upewnij się, że implementacja klienta testowego WCF dla tej usługi jest aktualny, kliknij prawym przyciskiem myszy usługę, a następnie wybierz katalog główny usługi **odświeżania usługi**. Należy pamiętać, że po odświeżeniu stan usługi jest resetowany.  
  
 Podczas proxy generowania, kompilowania binarnego lub wywołania usługi elementów menu, które obsługują odświeżanie usługi są wyłączone. Wywołania usługi jest niedostępne.  
  
## <a name="location-of-files-generated-by-the-test-client"></a>Lokalizacja plików wygenerowanych przez klienta testowego  
 Domyślnie magazynów klienta testowego WCF wygenerowanych plików kodu i Konfiguracja klienta w folderze "%appdata%\Local\temp\Test projektów klienckich". Ten folder jest usuwany po zamknięciu klienta testowego WCF. Jeśli plik konfiguracji zostanie zmodyfikowany w kliencie testowym WCF i **zawsze Generuj konfiguracji podczas uruchamiania usługi** opcja jest wyłączona, zmodyfikowany plik zostanie skopiowany do folderu "W pamięci podręcznej konfiguracji" w obszarze "Moje Documents\Test projektów klienckich Projektów klienckich Documents\Test"z pliku XML (metadanych adresów do nazwy pliku) mapowania jako indeks.  
  
 Można również uruchomić klienta testowego WCF w wierszu polecenia, użyj `/ProjectPath` przełącznika, aby określić nową ścieżkę odpowiednie do przechowywania plików wygenerowanych lub użyj `/RestoreProjectPath` przełącznik, aby przywrócić domyślną lokalizację. Składnia jest następująca:  
  
 `wcfTestClient.exe /ProjectPath [desired location]`  
  
 Uruchomienie tego polecenia nie jest otwierany klienta testowego WCF. Do lokalizacji folderu zostanie zmieniona. Czy klienta testowego WCF jest uruchomiona lub nie można uruchomić tego polecenia. Nowa lokalizacja jest stosowana po ponownym uruchomieniu klienta testowego WCF. Informacje o lokalizacji mogą zostać zapisane w rejestrze lub w pliku WcfTestClient.exe.option w folderze "%appdata%\Local\temp\Test projektów klienckich".  
  
## <a name="features-supported-by-wcf-test-client"></a>Funkcje obsługiwane przez klienta testowego WCF  
 Poniżej przedstawiono listę funkcji obsługiwanych przez klienta testowego WCF:  
  
-   Wywołania usługi: Żądanie/odpowiedź, a komunikat jednokierunkowy.  
  
-   Powiązania: obsługiwane przez Svcutil.exe wszystkie powiązania.  
  
-   Kontrolowanie sesji.  
  
-   Kontrakt komunikatu.  
  
-   Serializacja XML.  
  
 Poniżej przedstawiono listę funkcji nie są obsługiwane przez klienta testowego WCF:  
  
-   Typy: <xref:System.IO.Stream>, <xref:System.ServiceModel.Channels.Message>, <xref:System.Xml.XmlElement>, <xref:System.Xml.XmlAttribute>, <xref:System.Xml.XmlNode>, typy, które implementują <xref:System.Xml.Serialization.IXmlSerializable> interfejs, w tym pokrewny <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> atrybutu i <xref:System.Xml.Linq.XDocument> i <xref:System.Xml.Linq.XElement> typów i ADO.NET <xref:System.Data.DataTable> typu.  
  
-   Kontraktu dwukierunkowego.  
  
-   Transakcja.  
  
-   Zabezpieczenia: [!INCLUDE[infocard](../../../includes/infocard-md.md)] , certyfikatów i nazwy użytkownika i hasła.  
  
-   Powiązania: WSFederationbinding, wszelkie kontekst powiązania i powiązanie Https, WebHttpbinding (obsługi wiadomości odpowiedzi Json).  
  
## <a name="closing-wcf-test-client"></a>Zamykanie klienta testowego WCF  
 Możesz zamknąć klienta testowego WCF w następujący sposób:  
  
-   Na **pliku** menu, kliknij przycisk **zakończenia**. Alternatywnie w głównym oknie klienta testowego WCF, kliknij przycisk **Zamknij**. Zarówno z tych akcji również zamknięte Host automatycznie usługi WCF i zatrzymać proces debugowania programu Visual Studio, jeśli klienta testowego WCF została uruchomiona przez program Visual Studio.  
  
-   Kliknij prawym przyciskiem myszy **Host usługi WCF** ikonę w obszarze powiadomień, a następnie kliknij przycisk **zakończenia.** Zamyka klienta testowego WCF i hostów automatycznie usługi WCF i zatrzymuje programu Visual Studio debugowanie procesu.  
  
## <a name="see-also"></a>Zobacz też  
 [Host usługi WCF (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)

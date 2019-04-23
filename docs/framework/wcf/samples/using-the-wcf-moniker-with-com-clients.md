---
title: Używanie monikera programu WCF z klientami COM
ms.date: 03/30/2017
ms.assetid: e2799bfe-88bd-49d7-9d6d-ac16a9b16b04
ms.openlocfilehash: 14907dd3df66478e8f84b7735a84dd500855448b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59768387"
---
# <a name="using-the-wcf-moniker-with-com-clients"></a>Używanie monikera programu WCF z klientami COM
W tym przykładzie pokazano, jak użyć monikera programu Windows Communication Foundation (WCF) do integracji usług internetowych w środowiskach programistycznych opartych na modelu COM, takich jak Microsoft Office Visual Basic for Applications (VBA pakietu Office) lub Visual Basic 6.0. W tym przykładzie składa się z klienta Windows Script Host (VBS), obsługi klienta biblioteki (.dll) i usługi biblioteki (.dll), hostowanej przez Internetowe usługi informacyjne (IIS). Usługa jest usługą Kalkulator i klient modelu COM wywołuje operacji matematycznych — dodawania, odejmowania, mnożenia i dzielenia — w usłudze. Aktywność klienta jest widoczny w systemie windows okno komunikatu.  
  
> [!NOTE]
>  Procedury i kompilacja instrukcje dotyczące konfiguracji dla tego przykładu znajdują się na końcu tego tematu.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Interop\COM`  
  
 Implementuje usługi `ICalculator` kontrakt zdefiniowany jak pokazano w poniższym przykładzie kodu.  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface ICalculator  
{  
    [OperationContract]  
    double Add(double n1, double n2);  
    [OperationContract]  
    double Subtract(double n1, double n2);  
    [OperationContract]  
    double Multiply(double n1, double n2);  
    [OperationContract]  
    double Divide(double n1, double n2);  
}  
```  
  
 W przykładzie pokazano trzech alternatywnych metod dla używanie monikera programu:  
  
-   Wpisane kontraktu — jest zarejestrowany jako typ widoczne COM na komputerze klienckim.  
  
-   WSDL kontraktu — jest dostarczany w formie dokumentu WSDL.  
  
-   Wymiany metadanych kontraktu — są pobierane w czasie wykonywania z punktu końcowego metadanych programu Exchange (MEX).  
  
## <a name="typed-contract"></a>Wpisane kontraktu  
 Aby użyć monikera programu przy użyciu umowy wpisane, odpowiednio opartego na atrybutach typy kontraktu usługi musi być zarejestrowana w modelu COM. Po pierwsze, klient musi zostać wygenerowany przy użyciu [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). Uruchom następujące polecenie w wierszu polecenia w katalogu klienta można wygenerować typizowanego serwera proxy.  
  
```console  
svcutil.exe /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples http://localhost/servicemodelsamples/service.svc /out:generatedClient.cs  
```  
  
 Ta klasa muszą być zawarte w projekcie i projektu powinny być skonfigurowane do generowania modelu COM-widoczne, podpisanego zestawu podczas kompilowania. Plik AssemblyInfo.cs powinny być objęte następujący atrybut.  
  
```csharp
[assembly: ComVisible(true)]  
```  
  
 Po utworzeniu projektu, należy zarejestrować typy widoczne dla modelu COM za pomocą `regasm` jak pokazano w poniższym przykładzie.  
  
```console  
regasm.exe /tlb:CalcProxy.tlb client.dll  
```  
  
 Zestaw, który jest tworzony, należy dodać do globalnej pamięci podręcznej zestawów. Ściśle wymagane, ale upraszcza proces środowiska uruchomieniowego lokalizowanie zestawu. Następujące polecenie dodaje zestaw do globalnej pamięci podręcznej zestawów.  
  
```  
gacutil.exe /i client.dll  
```  
  
> [!NOTE]
>  Monikera programu wymaga tylko rejestracji typu, a nie za pomocą serwera proxy do komunikacji z usługą.  
  
 Aplikacja kliencka ComCalcClient.vbs używa `GetObject` funkcję, aby utworzyć serwer proxy dla usługi przy użyciu składni moniker usługi, aby określić adres, powiązanie i kontraktu usługi.  
  
```vbscript
Set typedServiceMoniker = GetObject(  
"service4:address=http://localhost/ServiceModelSamples/service.svc, binding=wsHttpBinding,   
contractType={9213C6D2-5A6F-3D26-839B-3BA9B82228D3}")  
```  
  
 Określ parametry używane przez moniker:  
  
-   Adres punktu końcowego usługi.  
  
-   Wiązanie, którego powinien używać klient do łączenia z tego punktu końcowego. W tym przypadku wsHttpBinding zdefiniowanych w systemie jest używany, chociaż można zdefiniować powiązań niestandardowych w plikach konfiguracji klienta. Do użytku z hostem skryptów Windows niestandardowego powiązania jest zdefiniowana w pliku Cscript.exe.config, w tym samym katalogu co Cscript.exe.  
  
-   Typ kontraktu, który jest obsługiwany w punkcie końcowym. Jest to typ, który został wygenerowany i zarejestrowany powyżej. Ponieważ skrypt Visual Basic nie udostępnia silnie typizowane COM środowiska, należy określić identyfikator dla kontraktu. Jest to identyfikator GUID `interfaceID` z CalcProxy.tlb, które mogą być wyświetlane za pomocą narzędzi COM, takich jak OLE/COM Object Viewer (OleView.exe). W środowiskach silnie typizowane, takich jak Office VBA lub Visual Basic 6.0 Dodawanie jawnego odwołania do biblioteki typów, a następnie deklarowania typu obiektu serwera proxy można zamiast parametru kontraktu. To ten zapewnia obsługę technologii IntelliSense podczas tworzenia aplikacji klienckich.  
  
 Posiadanie skonstruowany wystąpienia serwera proxy przy użyciu monikera programu, aplikacja kliencka może wywoływać metody na serwerze proxy, co skutkuje infrastruktury monikera usługi wywoływania odpowiednich operacji usługi.  
  
```vbscript  
' Call the service operations using the moniker object  
WScript.Echo "Typed service moniker: 100 + 15.99 = " & typedServiceMoniker.Add(100, 15.99)  
```  
  
 Po uruchomieniu przykładu, odpowiedź operacji jest wyświetlany w okno komunikatu Windows Script Host. W tym przykładzie pokazano, jak klient modelu COM, wywołań obiektów COM używanie monikera programu wpisane do komunikowania się z usługą WCF. Mimo zastosowania modelu COM w aplikacji klienckiej komunikacji z usługą składa się tylko z wywołania usługi sieci Web.  
  
## <a name="wsdl-contract"></a>Kontrakt WSDL  
 Moniker za pomocą kontraktu WSDL, nie rejestracji biblioteki klienta jest wymagany, ale musi zostać pobrany kontrakt WSDL dla usługi za pośrednictwem mechanizmu poza pasmem, takich jak otwieranie WSDL punktu końcowego usługi za pomocą przeglądarki. Moniker mogą uzyskiwać dostęp do tej Umowy w czasie wykonywania.  
  
 Aplikacja kliencka ComCalcClient.vbs używa `FileSystemObject` dostępu do pliku zapisanego lokalnie WSDL, a następnie ponownie używa `GetObject` funkcję, aby utworzyć serwer proxy dla usługi.  
  
```vbscript  
' Open the WSDL contract file and read it all into the wsdlContract string  
Const ForReading = 1  
Set objFSO = CreateObject("Scripting.FileSystemObject")  
Set objFile = objFSO.OpenTextFile("serviceWsdl.xml", ForReading)  
wsdlContract = objFile.ReadAll  
objFile.Close  
  
' Create a string for the service moniker including the content of the WSDL contract file  
wsdlMonikerString = "service4:address='http://localhost/ServiceModelSamples/service.svc'"  
wsdlMonikerString = wsdlMonikerString + ", binding=WSHttpBinding_ICalculator, bindingNamespace='http://Microsoft.ServiceModel.Samples'"  
wsdlMonikerString = wsdlMonikerString + ", wsdl='" & wsdlContract & "'"  
wsdlMonikerString = wsdlMonikerString + ", contract=ICalculator, contractNamespace='http://Microsoft.ServiceModel.Samples'"  
  
' Create the service moniker object  
Set wsdlServiceMoniker = GetObject(wsdlMonikerString)  
```  
  
 Określ parametry używane przez moniker:  
  
-   Adres punktu końcowego usługi.  
  
-   Wiązanie, którego powinien używać klient do połączenia z tego punktu końcowego i przestrzeni nazw, w którym to powiązanie jest zdefiniowany. W tym przypadku `wsHttpBinding_ICalculator` jest używany.  
  
-   Języka WSDL, który definiuje kontrakt. W tym przypadku jest to ciąg, który został odczytany z pliku serviceWsdl.xml.  
  
-   Nazwa i przestrzeni nazw kontraktu. Ten identyfikator jest wymagana, ponieważ WSDL może zawierać więcej niż jednego kontraktu.  
  
    > [!NOTE]
    >  Domyślnie usługi WCF generować oddzielne pliki WSDL dla każdej przestrzeni nazw, użycie. Są one połączone z użyciem konstrukcji importu WSDL. Ponieważ moniker oczekuje jednej definicji WSDL, jak pokazano w tym przykładzie Usługa należy użyć jednej przestrzeni nazw lub osobne pliki muszą zostać ręcznie połączone.  
  
 Posiadanie skonstruowany wystąpienia serwera proxy przy użyciu monikera programu, aplikacja kliencka może wywoływać metody na serwerze proxy, co skutkuje infrastruktury monikera usługi wywoływania odpowiednich operacji usługi.  
  
```vbscript  
' Call the service operations using the moniker object  
WScript.Echo "WSDL service moniker: 145 - 76.54 = " & wsdlServiceMoniker.Subtract(145, 76.54)  
```  
  
 Po uruchomieniu przykładu, odpowiedź operacji jest wyświetlany w okno komunikatu Windows Script Host. W tym przykładzie pokazano, jak klient modelu COM, wywołań obiektów COM używanie monikera programu za pomocą kontraktu WSDL do komunikowania się z usługą WCF.  
  
## <a name="metadata-exchange-contract"></a>Kontrakt wymiany metadanych  
 Za pomocą moniker kontrakt MEX zgodnie z umową WSDL nie klienta jest wymagana rejestracja. Kontrakt usługi są pobierane w czasie wykonywania za pomocą wewnętrznego wymiany metadanych.  
  
 Aplikacja kliencka ComCalcClient.vbs ponownie używa `GetObject` funkcję, aby utworzyć serwer proxy dla usługi.  
  
```vbscript  
' Create a string for the service moniker specifying the address to retrieve the service metadata from  
mexMonikerString = "service4:mexAddress='http://localhost/servicemodelsamples/service.svc/mex'"  
mexMonikerString = mexMonikerString + ", address='http://localhost/ServiceModelSamples/service.svc'"  
mexMonikerString = mexMonikerString + ", binding=WSHttpBinding_ICalculator, bindingNamespace='http://Microsoft.ServiceModel.Samples'"  
mexMonikerString = mexMonikerString + ", contract=ICalculator, contractNamespace='http://Microsoft.ServiceModel.Samples'"  
  
' Create the service moniker object  
Set mexServiceMoniker = GetObject(mexMonikerString)  
```  
  
 Określ parametry używane przez moniker:  
  
-   Adres punktu końcowego wymiany metadanych usługi.  
  
-   Adres punktu końcowego usługi.  
  
-   Wiązanie, którego powinien używać klient do połączenia z tego punktu końcowego i przestrzeni nazw, w którym to powiązanie jest zdefiniowany. W tym przypadku `wsHttpBinding_ICalculator` jest używany.  
  
-   Nazwa i przestrzeni nazw kontraktu. Ten identyfikator jest wymagana, ponieważ WSDL może zawierać więcej niż jednego kontraktu.  
  
 Posiadanie skonstruowany wystąpienia serwera proxy przy użyciu monikera programu, aplikacja kliencka może wywoływać metody na serwerze proxy, co skutkuje infrastruktury monikera usługi wywoływania odpowiednich operacji usługi.  
  
```vbscript  
' Call the service operations using the moniker object  
WScript.Echo "MEX service moniker: 9 * 81.25 = " & mexServiceMoniker.Multiply(9, 81.25)  
```  
  
 Po uruchomieniu przykładu, odpowiedź operacji jest wyświetlany w okno komunikatu Windows Script Host. W tym przykładzie pokazano, jak klient modelu COM, wywołań obiektów COM używanie monikera programu za pomocą kontraktu MEX do komunikowania się z usługą WCF.  
  
#### <a name="to-set-up-and-build-the-sample"></a>Aby skonfigurować i skompilować przykład  
  
1. Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. W wierszu polecenia dla deweloperów programu Visual Studio, otwórz folder \client\bin, w folderze specyficzny dla języka.  
  
    > [!NOTE]
    >  Jeśli używasz [!INCLUDE[wv](../../../../includes/wv-md.md)], [!INCLUDE[lserver](../../../../includes/lserver-md.md)], Windows 7 lub Windows Server 2008 R2, upewnij się, uruchom wiersz polecenia z uprawnieniami administratora.  
  
4. Wpisz `tlbexp.exe client.dll /out:CalcProxy.tlb` można wyeksportować biblioteki dll z plikiem tlb. "Ostrzeżenie eksportera biblioteki typów" oczekuje się, ale nie jest problemem, ponieważ typ ogólny nie jest wymagane.  
  
5. Wpisz `regasm.exe /tlb:CalcProxy.tlb client.dll` zarejestrować typy za pomocą modelu COM. "Ostrzeżenie eksportera biblioteki typów" oczekuje się, ale nie jest problemem, ponieważ typ ogólny nie jest wymagane.  
  
6. Wpisz `gacutil.exe /i client.dll` można dodać zestawu do globalnej pamięci podręcznej zestawów.  
  
#### <a name="to-run-the-sample-on-the-same-computer"></a>Aby uruchomić przykład na tym samym komputerze  
  
1. Test, który możesz uzyskać dostęp do usługi, w przeglądarce, wpisując następujący adres: `http://localhost/servicemodelsamples/service.svc`. Strona potwierdzenia powinna być wyświetlana w odpowiedzi.  
  
2. Uruchom ComCalcClient.vbs \client jest dostępna z folderu specyficzny dla języka. Aktywność klienta jest wyświetlana w polu wiadomości w systemie windows.  
  
3. Jeśli klient i usługa nie mogła nawiązać połączenia, zobacz [Rozwiązywanie problemów z porady dotyczące przykłady WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
#### <a name="to-run-the-sample-across-computers"></a>Do uruchomienia przykładu na komputerach  
  
1. Na komputerze usługi należy utworzyć katalog wirtualny o nazwie ServiceModelSamples. Skrypt Setupvroot.bat dołączone do przykładu może służyć do tworzenia katalogu na dysku i katalogu wirtualnego.  
  
2. Skopiuj pliki programu usługi z %SystemDrive%\Inetpub\wwwroot\servicemodelsamples katalog wirtualny ServiceModelSamples na komputerze usługi. Pamiętaj uwzględnić pliki w katalogu \bin.  
  
3. Skopiuj plik skryptu klienta z folderu \client w folderze specyficzny dla języka na komputerze klienckim.  
  
4. W pliku skryptu zmień wartość adresu definicji punktu końcowego, aby dopasować nowy adres usługi. Zastąp wszystkie odwołania do "localhost" w pełni kwalifikowaną nazwę domeny w adresie.  
  
5. Skopiuj plik WSDL na komputerze klienckim. W pliku WSDL serviceWsdl.xml, Zamień wszystkie odwołania do "localhost" w pełni kwalifikowaną nazwę domeny w adresie.  
  
6. Skopiuj bibliotekę Client.dll z folderu \client\bin w folderze specyficzny dla języka do katalogu na komputerze klienckim.  
  
7. W wierszu polecenia przejdź do tego katalogu docelowego na komputerze klienckim. Jeśli przy użyciu [!INCLUDE[wv](../../../../includes/wv-md.md)] lub [!INCLUDE[lserver](../../../../includes/lserver-md.md)], upewnij się uruchomić wiersz polecenia jako Administrator.  
  
8. Wpisz `tlbexp.exe client.dll /out:CalcProxy.tlb` można wyeksportować biblioteki dll z plikiem tlb. "Ostrzeżenie eksportera biblioteki typów" oczekuje się, ale nie jest problemem, ponieważ typ ogólny nie jest wymagane.  
  
9. Wpisz `regasm.exe /tlb:CalcProxy.tlb client.dll` zarejestrować typy za pomocą modelu COM. Upewnij się, ta ścieżka została ustawiona na folder, który zawiera `regasm.exe` przed uruchomieniem polecenia.  
  
10. Wpisz `gacutil.exe /i client.dll` można dodać zestawu do globalnej pamięci podręcznej zestawów. Upewnij się, ta ścieżka została ustawiona na folder, który zawiera `gacutil.exe` przed uruchomieniem polecenia.  
  
11. Test, aby uzyskać dostęp do usługi z poziomu komputera klienckiego za pomocą przeglądarki.  
  
12. Na komputerze klienckim, aby uruchomić ComCalcClient.vbs.  
  
#### <a name="to-clean-up-after-the-sample"></a>Aby wyczyścić zasoby po próbki  
  
-   Ze względów bezpieczeństwa usuń definicję katalogu wirtualnego i uprawnienia udzielone w ramach kroków konfiguracji, po zakończeniu pracy z próbek.  

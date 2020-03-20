---
title: Używanie monikera programu WCF z klientami COM
ms.date: 03/30/2017
ms.assetid: e2799bfe-88bd-49d7-9d6d-ac16a9b16b04
ms.openlocfilehash: d4d812c59a504f365eb3ad63ddd45ba5a66296e9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183236"
---
# <a name="using-the-wcf-moniker-with-com-clients"></a>Używanie monikera programu WCF z klientami COM
W tym przykładzie pokazano, jak używać moniker usługi Windows Communication Foundation (WCF) do integracji usług sieci Web w środowiskach programistycznych opartych na komismencie, takich jak Microsoft Office Visual Basic for Applications (Office VBA) lub Visual Basic 6.0. Ten przykład składa się z klienta hosta skryptów systemu Windows (vbs), pomocniczej biblioteki klienta (dll) i biblioteki usług (dll) hostowanego przez internetowe usługi informacyjne (IIS). Usługa jest usługą kalkulatora, a klient COM wywołuje operacje matematyczne — dodawanie, odejmowanie, mnożenie i dzielenie — w usłudze. Aktywność klienta jest widoczna w oknach okna okna okna komunikatu.  
  
> [!NOTE]
> Procedura konfiguracji i instrukcje kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
> [!IMPORTANT]
> Próbki mogą być już zainstalowane na komputerze. Przed kontynuowaniem sprawdź następujący (domyślny) katalog.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Interop\COM`  
  
 Usługa implementuje `ICalculator` kontrakt zdefiniowany w sposób pokazany w poniższym przykładzie kodu.  
  
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
  
 Przykład pokazuje trzy alternatywne podejścia do korzystania z monikera:  
  
- Typowa umowa — kontrakt jest zarejestrowany jako typ widoczny com na komputerze klienckim.  
  
- Umowa WSDL — umowa jest dostarczana w formie dokumentu WSDL.  
  
- Kontrakt wymiany metadanych — kontrakt jest pobierany w czasie wykonywania z punktu końcowego wymiany metadanych (MEX).  
  
## <a name="typed-contract"></a>Typowa umowa  
 Aby użyć monikera z typowym użyciem umowy, odpowiednio przypisane typy dla umowy serwisowej muszą być zarejestrowane w com. Po pierwsze, klient musi być generowany przy użyciu [narzędzia ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). Uruchom następujące polecenie z wiersza polecenia w katalogu klienta, aby wygenerować wpisany serwer proxy.  
  
```console  
svcutil.exe /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples http://localhost/servicemodelsamples/service.svc /out:generatedClient.cs  
```  
  
 Ta klasa musi być uwzględniona w projekcie, a projekt powinien być skonfigurowany do generowania zestawu widocznego dla urządzenia COM po skompilowaniu. W pliku AssemblyInfo.cs należy uwzględnić następujący atrybut.  
  
```csharp
[assembly: ComVisible(true)]  
```  
  
 Po zbudowaniu projektu zarejestruj typy widoczne `regasm` w programie COM przy użyciu jak pokazano w poniższym przykładzie.  
  
```console  
regasm.exe /tlb:CalcProxy.tlb client.dll  
```  
  
 Zestaw, który jest tworzony należy dodać do globalnej pamięci podręcznej zestawów. Chociaż nie jest to ściśle wymagane, upraszcza to proces środowiska wykonawczego lokalizowania zestawu. Następujące polecenie dodaje zestaw do globalnej pamięci podręcznej zestawów.  
  
```console  
gacutil.exe /i client.dll  
```  
  
> [!NOTE]
> Moniker usługi wymaga tylko rejestracji typu i nie używa serwera proxy do komunikowania się z usługą.  
  
 ComCalcClient.vbs aplikacja kliencka używa `GetObject` tej funkcji do konstruowania serwera proxy dla usługi, przy użyciu składni moniker usługi, aby określić adres, powiązanie i umowy dla usługi.  
  
```vbscript
Set typedServiceMoniker = GetObject(  
"service4:address=http://localhost/ServiceModelSamples/service.svc, binding=wsHttpBinding,
contractType={9213C6D2-5A6F-3D26-839B-3BA9B82228D3}")  
```  
  
 Parametry używane przez moniker określają:  
  
- Adres punktu końcowego usługi.  
  
- Powiązanie, które klient powinien używać do łączenia się z tym punktem końcowym. W takim przypadku zdefiniowane przez system wsHttpBinding jest używane, chociaż niestandardowe powiązania mogą być definiowane w plikach konfiguracji klienta. Do użytku z hostem skryptów systemu Windows powiązanie niestandardowe jest zdefiniowane w pliku Cscript.exe.config w tym samym katalogu co Cscript.exe.  
  
- Typ kontraktu, który jest obsługiwany w punkcie końcowym. Jest to typ, który został wygenerowany i zarejestrowany powyżej. Ponieważ skrypt języka Visual Basic nie zapewnia silnie typizowanego środowiska COM, należy określić identyfikator kontraktu. Ten identyfikator GUID jest `interfaceID` z CalcProxy.tlb, który można przeglądać za pomocą narzędzi COM, takich jak OLE/COM Object Viewer (OleView.exe). W przypadku silnie typizowanych środowisk, takich jak Office VBA lub Visual Basic 6.0, zamiast parametru kontraktu można dodać jawne odwołanie do biblioteki typów, a następnie zadeklarować typ obiektu serwera proxy. Zapewnia to również obsługę IntelliSense podczas tworzenia aplikacji klienckich.  
  
 Po skonstruowaniu wystąpienia serwera proxy za pomocą moniker usługi, aplikacja kliencka może wywołać metody na serwerze proxy, co powoduje infrastruktury moniker usługi wywołując odpowiednie operacje usługi.  
  
```vbscript  
' Call the service operations using the moniker object  
WScript.Echo "Typed service moniker: 100 + 15.99 = " & typedServiceMoniker.Add(100, 15.99)  
```  
  
 When you run the sample, the operation response is displayed in a Windows Script Host message box window. Pokazuje to klienta COM, który wywołuje COM przy użyciu wpisanego monikera do komunikowania się z usługą WCF. Pomimo użycia com w aplikacji klienckiej, komunikacja z usługą składa się tylko z wywołań usługi sieci Web.  
  
## <a name="wsdl-contract"></a>Kontrakt WSDL  
 Aby użyć moniker z umową WSDL, nie jest wymagana rejestracja biblioteki klienta, ale kontrakt WSDL dla usługi musi być pobierany za pośrednictwem mechanizmu poza pasmem, takiego jak korzystanie z przeglądarki w celu uzyskania dostępu do punktu końcowego WSDL dla usługi. Moniker może następnie uzyskać dostęp do tej umowy w czasie wykonywania.  
  
 ComCalcClient.vbs aplikacja kliencka `FileSystemObject` używa dostępu do lokalnie zapisanego pliku WSDL, a następnie ponownie używa `GetObject` funkcji do konstruowania serwera proxy dla usługi.  
  
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
  
 Parametry używane przez moniker określają:  
  
- Adres punktu końcowego usługi.  
  
- Powiązanie, które klient powinien używać do łączenia się z tym punktem końcowym i przestrzenią nazw, w której zdefiniowano to powiązanie. W takim przypadku `wsHttpBinding_ICalculator` jest używany.  
  
- WSDL, który definiuje kontrakt. W tym przypadku jest to ciąg, który został odczytany z pliku serviceWsdl.xml.  
  
- Nazwa i obszar nazw kontraktu. Ta identyfikacja jest wymagana, ponieważ WSDL może zawierać więcej niż jedną umowę.  
  
    > [!NOTE]
    > Domyślnie usługi WCF generują oddzielne pliki WSDL dla każdego obszaru nazw, który jest używany. Są one połączone z użyciem konstrukcji importu WSDL. Ponieważ moniker oczekuje pojedynczej definicji WSDL, usługa musi używać pojedynczego obszaru nazw, jak pokazano w tym przykładzie lub oddzielne pliki muszą być scalane ręcznie.  
  
 Po skonstruowaniu wystąpienia serwera proxy za pomocą moniker usługi, aplikacja kliencka może wywołać metody na serwerze proxy, co powoduje infrastruktury moniker usługi wywołując odpowiednie operacje usługi.  
  
```vbscript  
' Call the service operations using the moniker object  
WScript.Echo "WSDL service moniker: 145 - 76.54 = " & wsdlServiceMoniker.Subtract(145, 76.54)  
```  
  
 When you run the sample, the operation response is displayed in a Windows Script Host message box window. Pokazuje to klienta COM wykonywanie wywołań COM przy użyciu moniker z umowy WSDL do komunikowania się z usługą WCF.  
  
## <a name="metadata-exchange-contract"></a>Kontrakt wymiany metadanych  
 Aby użyć moniker z umową MEX, tak jak w przypadku umowy WSDL, nie jest wymagana rejestracja klienta. Kontrakt dla usługi jest pobierany w czasie wykonywania za pośrednictwem wewnętrznego użycia metadata Exchange.  
  
 ComCalcClient.vbs aplikacja kliencka `GetObject` ponownie używa funkcji do konstruowania serwera proxy dla usługi.  
  
```vbscript  
' Create a string for the service moniker specifying the address to retrieve the service metadata from  
mexMonikerString = "service4:mexAddress='http://localhost/servicemodelsamples/service.svc/mex'"  
mexMonikerString = mexMonikerString + ", address='http://localhost/ServiceModelSamples/service.svc'"  
mexMonikerString = mexMonikerString + ", binding=WSHttpBinding_ICalculator, bindingNamespace='http://Microsoft.ServiceModel.Samples'"  
mexMonikerString = mexMonikerString + ", contract=ICalculator, contractNamespace='http://Microsoft.ServiceModel.Samples'"  
  
' Create the service moniker object  
Set mexServiceMoniker = GetObject(mexMonikerString)  
```  
  
 Parametry używane przez moniker określają:  
  
- Adres punktu końcowego wymiany metadanych usługi.  
  
- Adres punktu końcowego usługi.  
  
- Powiązanie, które klient powinien używać do łączenia się z tym punktem końcowym i przestrzenią nazw, w której zdefiniowano to powiązanie. W takim przypadku `wsHttpBinding_ICalculator` jest używany.  
  
- Nazwa i obszar nazw kontraktu. Ta identyfikacja jest wymagana, ponieważ WSDL może zawierać więcej niż jedną umowę.  
  
 Po skonstruowaniu wystąpienia serwera proxy za pomocą moniker usługi, aplikacja kliencka może wywołać metody na serwerze proxy, co powoduje infrastruktury moniker usługi wywołując odpowiednie operacje usługi.  
  
```vbscript  
' Call the service operations using the moniker object  
WScript.Echo "MEX service moniker: 9 * 81.25 = " & mexServiceMoniker.Multiply(9, 81.25)  
```  
  
 When you run the sample, the operation response is displayed in a Windows Script Host message box window. Pokazuje to klienta COM wykonywanie wywołań COM przy użyciu moniker z umowy MEX do komunikowania się z usługą WCF.  
  
#### <a name="to-set-up-and-build-the-sample"></a>Aby skonfigurować i utworzyć próbkę  
  
1. Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Aby utworzyć wersję C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami w [tworzenie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. W wierszu polecenia dewelopera dla programu Visual Studio otwórz folder \client\bin w folderze specyficznym dla języka.  
  
    > [!NOTE]
    > Jeśli używasz systemu Windows Vista, Windows Server 2008, Windows 7 lub Windows Server 2008 R2, upewnij się, że wiersz polecenia jest uruchamiany z uprawnieniami administratora.  
  
4. Wpisz, `tlbexp.exe client.dll /out:CalcProxy.tlb` aby wyeksportować bibliotekę dll do pliku tlb. Oczekiwano "Ostrzeżenia eksportera biblioteki typu", ale nie jest to problem, ponieważ typ ogólny nie jest wymagany.  
  
5. Wpisz, `regasm.exe /tlb:CalcProxy.tlb client.dll` aby zarejestrować typy w COM. Oczekiwano "Ostrzeżenia eksportera biblioteki typu", ale nie jest to problem, ponieważ typ ogólny nie jest wymagany.  
  
6. `gacutil.exe /i client.dll` Wpisz, aby dodać zestaw do globalnej pamięci podręcznej zestawów.  
  
#### <a name="to-run-the-sample-on-the-same-computer"></a>Aby uruchomić próbkę na tym samym komputerze  
  
1. Sprawdź, czy możesz uzyskać dostęp do usługi za pomocą `http://localhost/servicemodelsamples/service.svc`przeglądarki, wpisując następujący adres: . W odpowiedzi powinna zostać wyświetlona strona potwierdzenia.  
  
2. Uruchom comcalcclient.vbs z \client, spod folderu specyficznego dla języka. Aktywność klienta jest wyświetlana w oknach okna okna komunikatu.  
  
3. Jeśli klient i usługa nie mogą się komunikować, zobacz [Porady dotyczące rozwiązywania problemów dla przykładów WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
#### <a name="to-run-the-sample-across-computers"></a>Aby uruchomić próbkę na różnych komputerach  
  
1. Na komputerze usługi utwórz katalog wirtualny o nazwie ServiceModelSamples. Skrypt Setupvroot.bat dołączony do przykładu może służyć do tworzenia katalogu dysku i katalogu wirtualnego.  
  
2. Skopiuj pliki programu serwisowego z %SystemDrive%\Inetpub\wwwroot\servicemodelsamples do katalogu wirtualnego ServiceModelSamples na komputerze usługi. Pamiętaj, aby dołączyć pliki do katalogu \bin.  
  
3. Skopiuj plik skryptu klienta z folderu \client w folderze specyficznym dla języka na komputer kliencki.  
  
4. W pliku skryptu zmień wartość adresu definicji punktu końcowego, aby dopasować go do nowego adresu usługi. Zastąp wszelkie odwołania do "localhost" w pełni kwalifikowaną nazwą domeny w adresie.  
  
5. Skopiuj plik WSDL na komputer kliencki. W pliku WSDL, serviceWsdl.xml, zastąp wszelkie odwołania do "localhost" w pełni kwalifikowaną nazwą domeny w adresie.  
  
6. Skopiuj bibliotekę Client.dll z folderu \client\bin w folderze specyficznym dla języka do katalogu na komputerze klienckim.  
  
7. W wierszu polecenia przejdź do tego katalogu docelowego na komputerze klienckim. Jeśli używasz systemu Windows Vista lub Windows Server 2008, uruchom wiersz polecenia jako administrator.  
  
8. Wpisz, `tlbexp.exe client.dll /out:CalcProxy.tlb` aby wyeksportować bibliotekę dll do pliku tlb. Oczekiwano "Ostrzeżenia eksportera biblioteki typu", ale nie jest to problem, ponieważ typ ogólny nie jest wymagany.  
  
9. Wpisz, `regasm.exe /tlb:CalcProxy.tlb client.dll` aby zarejestrować typy w COM. Przed uruchomieniem polecenia upewnij się, `regasm.exe` że ścieżka została ustawiona na folder, który zawiera.  
  
10. `gacutil.exe /i client.dll` Wpisz, aby dodać zestaw do globalnej pamięci podręcznej zestawów. Przed uruchomieniem polecenia upewnij się, `gacutil.exe` że ścieżka została ustawiona na folder, który zawiera.  
  
11. Sprawdź, czy można uzyskać dostęp do usługi z komputera klienckiego za pomocą przeglądarki.  
  
12. Na komputerze klienckim uruchom comcalcclient.vbs.  
  
#### <a name="to-clean-up-after-the-sample"></a>Aby oczyścić po próbce  
  
- Ze względów bezpieczeństwa usuń definicję katalogu wirtualnego i uprawnienia przyznane w krokach konfiguracji po zakończeniu pracy z próbkami.  

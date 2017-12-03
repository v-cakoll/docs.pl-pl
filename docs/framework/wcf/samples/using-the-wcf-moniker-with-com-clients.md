---
title: "Używanie monikera programu WCF z klientami COM"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e2799bfe-88bd-49d7-9d6d-ac16a9b16b04
caps.latest.revision: "34"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8a44ea352f5ff82294a9a28acb5a6b7f0730cf24
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="using-the-wcf-moniker-with-com-clients"></a>Używanie monikera programu WCF z klientami COM
W tym przykładzie przedstawiono sposób użycia [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] moniker usługi do integracji usług sieci Web w środowiskach Programowanie oparte na modelu COM, na przykład Microsoft Office Visual Basic for Applications (Office VBA) lub Visual Basic 6.0. W tym przykładzie składa się z klienta Host skryptów systemu Windows (VBS), pomocnicze biblioteki klienta (.dll) i usługi biblioteki (.dll), obsługiwane przez Internet Information Services (IIS). Usługa jest usługą Kalkulator i klient modelu COM wywołuje operacji matematycznych — Dodawanie, odjąć mnożenia i dzielenia — w usłudze. Aktywność klienta jest widoczny w systemie windows — okno komunikatu.  
  
> [!NOTE]
>  Procedury i kompilacji instrukcje dotyczące konfiguracji dla tego przykładu znajdują się na końcu tego tematu.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Interop\COM`  
  
 Implementuje usługi `ICalculator` kontrakt zdefiniowany, jak pokazano w poniższym przykładzie kodu.  
  
```  
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
  
 W przykładzie pokazano trzy alternatywnych metod dla przy użyciu krótkiej nazwy:  
  
-   Typu kontraktu — jest zarejestrowany jako typ widoczne COM na komputerze klienckim.  
  
-   Kontrakt WSDL — Umowa jest dostarczany w formie dokument WSDL.  
  
-   Wymiany metadanych kontraktu — są pobierane w czasie wykonywania z punktu końcowego metadanych programu Exchange (MEX).  
  
## <a name="typed-contract"></a>Typu kontraktu  
 Aby użyć monikerem przy użyciu typu kontraktu, odpowiednio oparte na atrybutach typów kontraktu usługi musi być zarejestrowana w modelu COM. Po pierwsze, klient musi zostać wygenerowany przy użyciu [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). Uruchom następujące polecenie w wierszu polecenia w katalogu klienta można wygenerować typu serwera proxy.  
  
```  
svcutil.exe /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples http://localhost/servicemodelsamples/service.svc /out:generatedClient.cs  
```  
  
 Ta klasa muszą być zawarte w projekcie i projekt powinien być skonfigurowany do generowania widoczny dla modelu COM, podpisany zestaw podczas kompilacji. Następujące atrybut powinien być uwzględniany w pliku AssemblyInfo.cs.  
  
```  
[assembly: ComVisible(true)]  
```  
  
 Po utworzeniu projektu należy zarejestrować typy widoczne dla modelu COM za pomocą `regasm` jak pokazano w poniższym przykładzie.  
  
```  
regasm.exe /tlb:CalcProxy.tlb client.dll  
```  
  
 Zestaw, który jest tworzony powinni zostać dodani do globalnej pamięci podręcznej zestawów. Nie są ściśle wymagane, ale upraszcza proces znajdowania zestawu środowiska wykonawczego. Polecenie dodaje zestaw do globalnej pamięci podręcznej zestawów.  
  
```  
gacutil.exe /i client.dll  
```  
  
> [!NOTE]
>  Moniker usługi wymaga tylko rejestracji typu i nie używa serwera proxy do komunikacji z usługą.  
  
 Aplikacja kliencka ComCalcClient.vbs używa `GetObject` funkcji, aby utworzyć serwer proxy dla usługi, określ adres, powiązanie, za pomocą składni krótkiej nazwy usługi i kontraktu usługi.  
  
```  
Set typedServiceMoniker = GetObject(  
"service4:address=http://localhost/ServiceModelSamples/service.svc, binding=wsHttpBinding,   
contractType={9213C6D2-5A6F-3D26-839B-3BA9B82228D3}")  
```  
  
 Podaj parametry używane przez moniker:  
  
-   Adres punktu końcowego usługi.  
  
-   Powiązania, które powinien używać klient do nawiązywania połączenia z tym punktem końcowym. W takim przypadku wsHttpBinding zdefiniowana w systemie jest używany, chociaż można zdefiniować powiązania niestandardowe w plikach konfiguracji klienta. Do użytku z hostem skryptów systemu Windows niestandardowego powiązania jest zdefiniowany w pliku Cscript.exe.config w tym samym katalogu co Cscript.exe.  
  
-   Typ kontraktu, który jest obsługiwany w punkcie końcowym. Jest to typ, który został wygenerowany i zarejestrowana powyżej. Ponieważ skrypt Visual Basic nie zapewnia środowisku jednoznacznie modelu COM, należy określić identyfikator umowy. Ten identyfikator GUID jest `interfaceID` z CalcProxy.tlb, które można wyświetlić przy użyciu narzędzia COM, takie jak przeglądarka obiektów OLE/COM (OleView.exe). W środowiskach jednoznacznie, takich jak Office VBA lub Visual Basic 6.0 dodanie jawnego odwołania do biblioteki typów, a następnie deklarowanie typu obiektu serwera proxy można użyć zamiast parametrów kontraktu. Zapewnia również obsługę funkcji IntelliSense podczas tworzenia aplikacji klienta.  
  
 O utworzone wystąpienie serwera proxy z monikerem usługi, aplikacji klienckiej, można wywoływać metod na serwerze proxy, co powoduje wywołanie odpowiednich operacji usługi infrastruktury moniker usługi.  
  
```  
' Call the service operations using the moniker object  
WScript.Echo "Typed service moniker: 100 + 15.99 = " & typedServiceMoniker.Add(100, 15.99)  
```  
  
 Po uruchomieniu próbki odpowiedzi operacji jest wyświetlany w okno komunikatu Host skryptów systemu Windows. Oznacza to, klient modelu COM wywołań obiektów COM za pomocą typu krótkiej nazwy do komunikowania się z [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi. Niezależnie od stosowania modelu COM w aplikacji klienckiej komunikacja z usługą składa się tylko z wywołania usługi sieci Web.  
  
## <a name="wsdl-contract"></a>Kontrakt WSDL  
 Aby użyć monikerem z kontraktem WSDL, nie klienta biblioteki jest wymagana rejestracja, ale kontrakt WSDL dla usługi musi zostać pobrane za pośrednictwem mechanizmu poza pasmem, takie jak otwieranie WSDL punktu końcowego usługi za pomocą przeglądarki. Następnie moniker mają dostęp do tego kontraktu w czasie wykonywania.  
  
 Aplikacja kliencka ComCalcClient.vbs używa `FileSystemObject` dostępu lokalnie zapisanego pliku WSDL, a następnie ponownie używa `GetObject` funkcji do utworzenia serwera proxy dla usługi.  
  
```  
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
  
 Podaj parametry używane przez moniker:  
  
-   Adres punktu końcowego usługi.  
  
-   Powiązania, które powinien używać klient do nawiązywania połączenia z określonego punktu końcowego i przestrzeni nazw, w którym jest zdefiniowany tego powiązania. W takim przypadku `wsHttpBinding_ICalculator` jest używany.  
  
-   WSDL, który definiuje kontrakt. W tym przypadku jest to ciąg, który został odczytany z pliku serviceWsdl.xml.  
  
-   Nazwa i przestrzeń nazw kontraktu. Ten identyfikator jest wymagana, ponieważ WSDL może zawierać więcej niż jeden kontrakt.  
  
    > [!NOTE]
    >  Domyślnie [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi generować oddzielne pliki WSDL dla każdej przestrzeni nazw który użycia. Są połączone z użyciem konstrukcji importu WSDL. Ponieważ moniker oczekuje jednej definicji WSDL, usługa musi użyć jedna przestrzeń nazw jak pokazano w przykładzie lub osobne pliki muszą zostać ręcznie połączone.  
  
 O utworzone wystąpienie serwera proxy z monikerem usługi, aplikacji klienckiej, można wywoływać metod na serwerze proxy, co powoduje wywołanie odpowiednich operacji usługi infrastruktury moniker usługi.  
  
```  
' Call the service operations using the moniker object  
WScript.Echo "WSDL service moniker: 145 - 76.54 = " & wsdlServiceMoniker.Subtract(145, 76.54)  
```  
  
 Po uruchomieniu próbki odpowiedzi operacji jest wyświetlany w okno komunikatu Host skryptów systemu Windows. Oznacza to, klient modelu COM wywołań obiektów COM za pomocą krótkiej nazwy z kontraktem WSDL do komunikowania się z [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi.  
  
## <a name="metadata-exchange-contract"></a>Kontrakt wymiany metadanych  
 Aby użyć monikerem z kontrakt MEX zgodnie z umową WSDL nie klienta jest wymagana rejestracja. Kontrakt usługi są pobierane w czasie wykonywania za pomocą wewnętrznego wymiany metadanych.  
  
 Aplikacja kliencka ComCalcClient.vbs ponownie używa `GetObject` funkcji do utworzenia serwera proxy dla usługi.  
  
```  
' Create a string for the service moniker specifying the address to retrieve the service metadata from  
mexMonikerString = "service4:mexAddress='http://localhost/servicemodelsamples/service.svc/mex'"  
mexMonikerString = mexMonikerString + ", address='http://localhost/ServiceModelSamples/service.svc'"  
mexMonikerString = mexMonikerString + ", binding=WSHttpBinding_ICalculator, bindingNamespace='http://Microsoft.ServiceModel.Samples'"  
mexMonikerString = mexMonikerString + ", contract=ICalculator, contractNamespace='http://Microsoft.ServiceModel.Samples'"  
  
' Create the service moniker object  
Set mexServiceMoniker = GetObject(mexMonikerString)  
```  
  
 Podaj parametry używane przez moniker:  
  
-   Adres punktu końcowego wymiany metadanych usługi.  
  
-   Adres punktu końcowego usługi.  
  
-   Powiązania, które powinien używać klient do nawiązywania połączenia z określonego punktu końcowego i przestrzeni nazw, w którym jest zdefiniowany tego powiązania. W takim przypadku `wsHttpBinding_ICalculator` jest używany.  
  
-   Nazwa i przestrzeń nazw kontraktu. Ten identyfikator jest wymagana, ponieważ WSDL może zawierać więcej niż jeden kontrakt.  
  
 O utworzone wystąpienie serwera proxy z monikerem usługi, aplikacji klienckiej, można wywoływać metod na serwerze proxy, co powoduje wywołanie odpowiednich operacji usługi infrastruktury moniker usługi.  
  
```  
' Call the service operations using the moniker object  
WScript.Echo "MEX service moniker: 9 * 81.25 = " & mexServiceMoniker.Multiply(9, 81.25)  
```  
  
 Po uruchomieniu próbki odpowiedzi operacji jest wyświetlany w okno komunikatu Host skryptów systemu Windows. Oznacza to, klient modelu COM wywołań obiektów COM za pomocą krótkiej nazwy z kontraktem MEX do komunikowania się z [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi.  
  
#### <a name="to-set-up-and-build-the-sample"></a>Aby skonfigurować i tworzyć przykładowy kod  
  
1.  Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Z [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] wiersz polecenia, otwórz folder \client\bin, w folderze danego języka.  
  
    > [!NOTE]
    >  Jeśli używasz [!INCLUDE[wv](../../../../includes/wv-md.md)], [!INCLUDE[lserver](../../../../includes/lserver-md.md)], Windows 7 lub Windows Server 2008 R2, upewnij się, uruchom wiersz polecenia z uprawnieniami administratora.  
  
4.  Wpisz `tlbexp.exe client.dll /out:CalcProxy.tlb` można wyeksportować do pliku tlb biblioteki dll. "Ostrzeżenie eksportera biblioteki typów" jest oczekiwany, ale nie stanowi to problemu, ponieważ typ ogólny nie jest wymagane.  
  
5.  Wpisz `regasm.exe /tlb:CalcProxy.tlb client.dll` zarejestrować typy z modelu COM. "Ostrzeżenie eksportera biblioteki typów" jest oczekiwany, ale nie stanowi to problemu, ponieważ typ ogólny nie jest wymagane.  
  
6.  Wpisz `gacutil.exe /i client.dll` można dodać zestawu do globalnej pamięci podręcznej zestawów.  
  
#### <a name="to-run-the-sample-on-the-same-computer"></a>Aby uruchomić przykład na tym samym komputerze  
  
1.  Test, który można uzyskać dostępu do usługi przy użyciu przeglądarki przez wpisanie następującego adresu: `http://localhost/servicemodelsamples/service.svc`. Powinna być wyświetlana strona potwierdzenia w odpowiedzi.  
  
2.  Uruchom ComCalcClient.vbs z \client z folderu specyficzny dla języka. Aktywność klienta jest wyświetlany w systemie windows — okno komunikatu.  
  
3.  Jeśli klient i usługa nie będą mogli komunikować się, zobacz [Rozwiązywanie problemów z porady](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).  
  
#### <a name="to-run-the-sample-across-computers"></a>Aby uruchomić przykład na komputerach  
  
1.  Na komputerze, usługi należy utworzyć katalog wirtualny o nazwie ServiceModelSamples. Skrypt Setupvroot.bat dołączony próbki mogą służyć do tworzenia katalogu na dysku i katalog wirtualny.  
  
2.  Skopiuj pliki programu usługi z %SystemDrive%\Inetpub\wwwroot\servicemodelsamples do katalogu wirtualnego ServiceModelSamples na komputerze usługi. Pamiętaj uwzględnić pliki w katalogu \bin.  
  
3.  Skopiuj plik skryptu klienta z folderu \client w folderze danego języka na komputerze klienckim.  
  
4.  W pliku skryptu zmień wartość adresu definicji punktu końcowego do dopasowania nowy adres z usługą. Zamień wszystkie odwołania do "localhost" pełni kwalifikowanej nazwy domeny w adresie.  
  
5.  Skopiuj plik WSDL na komputerze klienckim. W pliku WSDL serviceWsdl.xml, Zamień wszystkie odwołania do "localhost" pełni kwalifikowanej nazwy domeny w adresie.  
  
6.  Kopiowanie biblioteki Client.dll z folderu \client\bin w folderze danego języka do katalogu na komputerze klienckim.  
  
7.  W wierszu polecenia przejdź do tego katalogu docelowego na komputerze klienckim. Jeśli przy użyciu [!INCLUDE[wv](../../../../includes/wv-md.md)] lub [!INCLUDE[lserver](../../../../includes/lserver-md.md)], upewnij się uruchomić wiersz polecenia jako Administrator.  
  
8.  Wpisz `tlbexp.exe client.dll /out:CalcProxy.tlb` można wyeksportować do pliku tlb biblioteki dll. "Ostrzeżenie eksportera biblioteki typów" jest oczekiwany, ale nie stanowi to problemu, ponieważ typ ogólny nie jest wymagane.  
  
9. Wpisz `regasm.exe /tlb:CalcProxy.tlb client.dll` zarejestrować typy z modelu COM. Upewnij się, że ścieżka została ustawiona jako folder zawierający `regasm.exe` przed uruchomieniem polecenia.  
  
10. Wpisz `gacutil.exe /i client.dll` można dodać zestawu do globalnej pamięci podręcznej zestawów. Upewnij się, że ścieżka została ustawiona jako folder zawierający `gacutil.exe` przed uruchomieniem polecenia.  
  
11. Aby uzyskać dostęp do usługi z komputera klienckiego przy użyciu przeglądarki testu.  
  
12. Na komputerze klienckim uruchom ComCalcClient.vbs.  
  
#### <a name="to-clean-up-after-the-sample"></a>Aby wyczyścić po próbki  
  
-   Ze względów bezpieczeństwa Usuń katalog wirtualny definicji i uprawnienia przyznane w ramach kroków konfiguracji, po zakończeniu pracy z próbek.  
  
## <a name="see-also"></a>Zobacz też

---
title: Dostęp do usług WCF za pomocą aplikacji klienckiej ze Sklepu Windows
ms.date: 03/30/2017
ms.assetid: e2002ef4-5dee-4a54-9d87-03b33d35fc52
ms.openlocfilehash: ff6638936f476bd8fe75a065d3e61e96790cb7f4
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597699"
---
# <a name="accessing-wcf-services-with-a-windows-store-client-app"></a>Dostęp do usług WCF za pomocą aplikacji klienckiej ze Sklepu Windows
System Windows 8 wprowadza nowy typ aplikacji o nazwie aplikacje ze sklepu Windows. Te aplikacje są projektowane wokół interfejsu ekranu dotykowego. .NET Framework 4,5 umożliwia aplikacjom ze sklepu Windows wywoływanie usług WCF.  
  
## <a name="wcf-support-in-windows-store-applications"></a>Obsługa platformy WCF w aplikacjach ze sklepu Windows  
 Podzestaw funkcji WCF jest dostępny w aplikacji ze sklepu Windows. więcej informacji znajduje się w poniższych sekcjach.  
  
> [!IMPORTANT]
> Użyj interfejsów API zespalania zamiast tych, które są udostępniane przez platformę WCF. Aby uzyskać więcej informacji, zobacz [interfejs API zespalania programu WinRT](xref:Windows.Web.Syndication)  
  
> [!WARNING]
> Dodawanie odwołania do usługi sieci Web do składnika środowisko wykonawcze systemu Windows przy użyciu Dodaj odwołanie do usługi nie jest obsługiwane.  
  
### <a name="supported-bindings"></a>Obsługiwane powiązania  
 W aplikacjach ze sklepu Windows obsługiwane są następujące powiązania WCF:  
  
1. <xref:System.ServiceModel.BasicHttpBinding>  
  
2. <xref:System.ServiceModel.NetTcpBinding>  
  
3. <xref:System.ServiceModel.NetHttpBinding>  
  
4. <xref:System.ServiceModel.Channels.CustomBinding>
  
 Następujące elementy powiązania są obsługiwane w aplikacjach ze sklepu Windows  
  
1. <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>  
  
2. <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>  
  
3. <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement>  
  
4. <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>  
  
5. <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>  
  
6. <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
  
7. <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
  
8. <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
  
9. <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>  
  
 Obsługiwane są zarówno kodowanie tekstu, jak i binarne. Obsługiwane są wszystkie tryby transferu WCF. Aby uzyskać więcej informacji, zobacz [transfer komunikatów przesyłanych strumieniowo](streaming-message-transfer.md).  
  
### <a name="add-service-reference"></a>Dodaj odwołanie do usługi  
 Aby wywołać usługę WCF z poziomu aplikacji ze sklepu Windows, użyj funkcji Dodaj odwołanie do usługi programu Visual Studio 2012. Po wykonaniu tej czynności w aplikacji ze sklepu Windows zobaczysz kilka zmian w funkcji Dodaj odwołanie do usługi. Nie jest generowany pierwszy plik konfiguracji. Aplikacje ze sklepu Windows nie używają plików konfiguracji, dlatego muszą być skonfigurowane w kodzie. Ten kod konfiguracji można znaleźć w pliku References.cs generowanym przez Dodaj odwołanie do usługi. Aby wyświetlić ten plik, upewnij się, że wybrano opcję "Pokaż wszystkie pliki" w Eksploratorze rozwiązań. Plik będzie znajdował się w ramach odwołań do usługi, a następnie odwołuje się do węzłów. svcmap w ramach projektu. Wszystkie operacje wygenerowane dla usług WCF w ramach aplikacji ze sklepu Windows będą asynchroniczne za pomocą wzorca asynchronicznego opartego na zadaniach. Aby uzyskać więcej informacji, zobacz [zadania asynchroniczne — uproszczenie programowania asynchronicznego z zadaniami](https://docs.microsoft.com/archive/msdn-magazine/2010/september/async-tasks-simplify-asynchronous-programming-with-tasks).  
  
 Ponieważ konfiguracja jest teraz generowana w kodzie, wszelkie zmiany wprowadzone w pliku Reference.cs zostałyby zastępować za każdym razem, gdy odwołanie do usługi zostanie zaktualizowane. Aby wyeliminować tę sytuację, kod konfiguracji jest generowany w ramach metody częściowej, którą można zaimplementować w klasie proxy klienta. Metoda częściowa jest zadeklarowana w następujący sposób:  
  
```csharp  
static partial void Configure(System.ServiceModel.Description.ServiceEndpoint serviceEndpoint,  
            System.ServiceModel.Description.ClientCredentials clientCredentials);  
```  
  
 Następnie można zaimplementować tę metodę częściową i zmienić powiązanie lub punkt końcowy w klasie proxy klienta w następujący sposób:  
  
```csharp  
public partial class Service1Client : System.ServiceModel.ClientBase<MetroWcfClient.ServiceRefMultiEndpt.IService1>, MetroWcfClient.ServiceRefMultiEndpt.IService1  
    {
        static partial void Configure(System.ServiceModel.Description.ServiceEndpoint serviceEndpoint,
            System.ServiceModel.Description.ClientCredentials clientCredentials)  
        {  
            if (serviceEndpoint.Name ==
                    ServiceRefMultiEndpt.Service1Client.EndpointConfiguration.BasicHttpBinding_IService1.ToString())  
            {  
                serviceEndpoint.Binding.SendTimeout = new System.TimeSpan(0, 1, 0);  
            }  
            else if (serviceEndpoint.Name ==
                    ServiceRefMultiEndpt.Service1Client.EndpointConfiguration.BasicHttpBinding_IService11.ToString())  
            {  
                serviceEndpoint.Binding.SendTimeout = new System.TimeSpan(0, 1, 0);  
                clientCredentials.UserName.UserName = "username1";  
                clientCredentials.UserName.Password = "password";  
            }  
            else if (serviceEndpoint.Name ==
                    ServiceRefMultiEndpt.Service1Client.EndpointConfiguration.NetTcpBinding_IService1.ToString())  
            {  
                serviceEndpoint.Binding.Name = "MyTcpBinding";  
                serviceEndpoint.Address = new System.ServiceModel.EndpointAddress("net.tcp://localhost/tcp");  
            }  
        }  
    }  
```  
  
### <a name="serialization"></a>Serializacja  
 Następujące serializatory są obsługiwane w aplikacjach ze sklepu Windows:  
  
1. DataContractSerializer  
  
2. Klasa DataContractJsonSerializer  
  
3. XmlSerializer  
  
> [!WARNING]
> Implementacja obiektu XmlDictionaryWriter. Write (DateTime) teraz zapisuje obiekt DateTime jako ciąg.  
  
### <a name="security"></a>Zabezpieczenia  

W aplikacjach ze sklepu Windows obsługiwane są następujące tryby zabezpieczeń:
  
1. <xref:System.ServiceModel.SecurityMode.None>  
  
2. <xref:System.ServiceModel.SecurityMode.Transport>  
  
3. <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>
  
4. <xref:System.ServiceModel.SecurityMode.Message>
  
Następujące typy poświadczeń klienta są obsługiwane w aplikacjach ze sklepu Windows:
  
1. Brak  
  
2. Podstawowy  
  
3. Szyfrowane  
  
4. Negotiate  
  
5. NTLM  
  
6. Windows  
  
7. Nazwa użytkownika (zabezpieczenia komunikatów)  
  
8. Windows (Transport Security)  
  
 Aby aplikacje ze sklepu Windows mogły uzyskiwać dostęp do domyślnych poświadczeń systemu Windows i je wysyłać, należy włączyć tę funkcję w pliku Package. Appmanifest. Otwórz ten plik i wybierz kartę możliwości i wybierz pozycję "domyślne poświadczenia systemu Windows". Umożliwia to aplikacji łączenie się z zasobami intranetowymi, które wymagają poświadczeń domeny.  
  
> [!IMPORTANT]
> Aby aplikacje ze sklepu Windows mogły wykonywać wywołania między maszynami, należy włączyć inną możliwość nazywaną "siecią domową/służbową". To ustawienie znajduje się również w pliku Package. Appmanifest na karcie możliwości. Zaznacz pole wyboru Sieć domowa/Work. Zapewnia to aplikacji dostęp przychodzący i wychodzący do sieci zaufanych miejsc użytkownika, takich jak Home i Work. Przychodzące porty krytyczne są zawsze blokowane. Aby uzyskać dostęp do usług w Internecie, należy również włączyć funkcję internetową (klienta).  
  
### <a name="misc"></a>Różne  
 Użycie następujących klas jest obsługiwane w przypadku aplikacji ze sklepu Windows:  
  
1. <xref:System.ServiceModel.ChannelFactory>  
  
2. <xref:System.ServiceModel.DuplexChannelFactory%601>
  
3. <xref:System.ServiceModel.CallbackBehaviorAttribute>  
  
### <a name="defining-service-contracts"></a>Definiowanie kontraktów usługi  
 Zalecamy tylko Definiowanie asynchronicznych operacji usługi przy użyciu wzorca asynchronicznego opartego na zadaniach. Dzięki temu aplikacje ze sklepu Windows pozostają w stanie reagować podczas wywoływania operacji usługi.  
  
> [!WARNING]
> Chociaż wyjątek nie zostanie wygenerowany, jeśli zdefiniujesz operację synchroniczną, zdecydowanie zaleca się tylko zdefiniowanie operacji asynchronicznych.  
  
### <a name="calling-wcf-services-from-windows-store-applications"></a>Wywoływanie usług WCF z aplikacji ze sklepu Windows  
 Jak wspomniano wcześniej, przed całą konfiguracją należy wykonać w kodzie w metodzie GetBindingForEndpoint w wygenerowanej klasie proxy. Wywoływanie operacji usługi odbywa się tak samo jak wywołanie metody asynchronicznej opartej na zadaniach, jak pokazano w poniższym fragmencie kodu.  
  
```csharp  
void async SomeMethod()  
{  
    ServiceClient proxy = new ServiceClient();  
    Task<T> results = await proxy.CallAsync(param1, param2);  
    T result = results.Result;  
    if (result.Success)  
    {  
       // Do something with result  
    }  
}  
```  
  
 Zwróć uwagę na użycie słowa kluczowego Async na metodzie wywołującym wywołanie asynchroniczne i słowo kluczowe await podczas wywoływania metody asynchronicznej.  
  
## <a name="see-also"></a>Zobacz też

- [Blog usługi WCF w Sklepie Windows](https://docs.microsoft.com/archive/blogs/piyushjo/wcf-in-windows-8-metro-styled-apps-absolutely-supported)
- [Klienci i zabezpieczenia sklepu Windows WCF](https://docs.microsoft.com/archive/blogs/piyushjo/calling-a-wcf-service-from-a-metro-application-adding-security)
- [Aplikacje ze sklepu Windows i wywołania między maszynami](https://docs.microsoft.com/archive/blogs/piyushjo/calling-a-wcf-service-from-a-metro-application-cross-machine-scenario)
- [Wywoływanie usługi WCF wdrożonej na platformie Azure z aplikacji ze sklepu Windows](https://docs.microsoft.com/archive/blogs/piyushjo/calling-a-wcf-service-from-a-metro-application-cross-machine-scenario)
- [Programowanie zabezpieczeń WCF](programming-wcf-security.md)
- [Powiązania](../bindings.md)

---
title: Dostęp do usług WCF za pomocą aplikacji klienckiej ze Sklepu Windows
ms.date: 03/30/2017
ms.assetid: e2002ef4-5dee-4a54-9d87-03b33d35fc52
ms.openlocfilehash: b4b91c103aa91e3b2c9e811c642a8347c7db1a88
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185481"
---
# <a name="accessing-wcf-services-with-a-windows-store-client-app"></a>Dostęp do usług WCF za pomocą aplikacji klienckiej ze Sklepu Windows
System Windows 8 wprowadza nowy typ aplikacji o nazwie Aplikacje ze Sklepu Windows. Aplikacje te są zaprojektowane wokół interfejsu ekranu dotykowego. Program .NET Framework 4.5 umożliwia aplikacjom ze Sklepu Windows wywoływanie usług WCF.  
  
## <a name="wcf-support-in-windows-store-applications"></a>Obsługa WCF w aplikacjach ze Sklepu Windows  
 Podzbiór funkcji WCF jest dostępny z poziomu aplikacji ze Sklepu Windows, zobacz poniższe sekcje, aby uzyskać więcej informacji.  
  
> [!IMPORTANT]
> Użyj interfejsów API syndykacji WinRT zamiast interfejsów zainteresowanych przez WCF. Aby uzyskać więcej informacji, zobacz [WinRT Syndication API](xref:Windows.Web.Syndication)  
  
> [!WARNING]
> Dodawanie odwołania do usługi w celu dodania odwołania do usługi sieci Web do składnika środowiska wykonawczego systemu Windows nie jest obsługiwane.  
  
### <a name="supported-bindings"></a>Obsługiwane powiązania  
 Następujące powiązania WCF są obsługiwane w aplikacjach ze Sklepu Windows:  
  
1. <xref:System.ServiceModel.BasicHttpBinding>  
  
2. <xref:System.ServiceModel.NetTcpBinding>  
  
3. <xref:System.ServiceModel.NetHttpBinding>  
  
4. <xref:System.ServiceModel.Channels.CustomBinding>
  
 Następujące elementy wiązania są obsługiwane w aplikacjach ze Sklepu Windows  
  
1. <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>  
  
2. <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>  
  
3. <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement>  
  
4. <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>  
  
5. <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>  
  
6. <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
  
7. <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
  
8. <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
  
9. <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>  
  
 Obsługiwane są kodowania tekstowe i binarne. Obsługiwane są wszystkie tryby transferu WCF. Aby uzyskać więcej informacji, zobacz [Przesyłanie strumieniowe wiadomości](../../../../docs/framework/wcf/feature-details/streaming-message-transfer.md).  
  
### <a name="add-service-reference"></a>Dodaj dokumentację usługi  
 Aby wywołać usługę WCF z aplikacji ze Sklepu Windows, należy użyć funkcji Dodaj odwołanie do usługi programu Visual Studio 2012. Można zauważyć kilka zmian w funkcjonalności Dodaj odwołanie do usługi, gdy odbywa się w aplikacji ze Sklepu Windows. Najpierw nie jest generowany żaden plik konfiguracyjny. Aplikacje ze Sklepu Windows nie używają plików konfiguracyjnych, więc muszą być skonfigurowane w kodzie. Ten kod konfiguracji można znaleźć w pliku References.cs wygenerowanym przez dodaj odwołanie do usługi. Aby wyświetlić ten plik, upewnij się, że w Eksploratorze rozwiązań wybierz opcję "Pokaż wszystkie pliki". Plik będzie znajdować się w obszarze Odwołania do usługi, a następnie węzły Reference.svcmap w ramach projektu. Wszystkie operacje generowane dla usług WCF w aplikacji Ze Sklepu Windows będą asynchroniczne przy użyciu wzorca asynchronicznego opartego na zadaniach. Aby uzyskać więcej informacji, zobacz [Zadania asynchroniczne — upraszczanie programowania asynchroniczne z zadaniami](https://docs.microsoft.com/archive/msdn-magazine/2010/september/async-tasks-simplify-asynchronous-programming-with-tasks).  
  
 Ponieważ konfiguracja jest teraz generowana w kodzie, wszelkie zmiany wprowadzone w pliku Reference.cs zostaną zastąpione za każdym razem, gdy odwołanie do usługi jest aktualizowane. Aby zaradzić tej sytuacji kod konfiguracji jest generowany w ramach metody częściowej, które można zaimplementować w klasie serwera proxy klienta. Metoda częściowa jest zadeklarowana w następujący sposób:  
  
```csharp  
static partial void Configure(System.ServiceModel.Description.ServiceEndpoint serviceEndpoint,  
            System.ServiceModel.Description.ClientCredentials clientCredentials);  
```  
  
 Następnie można zaimplementować tę metodę częściową i zmienić powiązanie lub punkt końcowy w klasie serwera proxy klienta w następujący sposób:  
  
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
 W aplikacjach ze Sklepu Windows obsługiwane są następujące serializatory:  
  
1. DataContractSerializer  
  
2. Datacontractjsonserializer  
  
3. Xmlserializer  
  
> [!WARNING]
> XmlDictionaryWriter.Write(DateTime) teraz zapisuje DateTime obiektu jako ciąg.  
  
### <a name="security"></a>Zabezpieczenia  

W aplikacjach ze Sklepu Windows są obsługiwane następujące tryby zabezpieczeń:
  
1. <xref:System.ServiceModel.SecurityMode.None>  
  
2. <xref:System.ServiceModel.SecurityMode.Transport>  
  
3. <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>
  
4. <xref:System.ServiceModel.SecurityMode.Message>
  
Następujące typy poświadczeń klienta są obsługiwane w aplikacjach ze Sklepu Windows:
  
1. Brak  
  
2. Podstawowa (Basic)  
  
3. Szyfrowane  
  
4. Negotiate  
  
5. NTLM  
  
6. Windows  
  
7. Nazwa użytkownika (zabezpieczenia wiadomości)  
  
8. Windows (zabezpieczenia transportu)  
  
 Aby aplikacje ze Sklepu Windows uzyskiwano dostęp do domyślnych poświadczeń systemu Windows i wysyłać je, należy włączyć tę funkcję w pliku Package.appmanifest. Otwórz ten plik i wybierz kartę Możliwości i wybierz "Domyślne poświadczenia systemu Windows". Dzięki temu aplikacja może łączyć się z zasobami intranetowymi, które wymagają poświadczeń domeny.  
  
> [!IMPORTANT]
> Aby aplikacje ze Sklepu Windows do wykonywania połączeń między komputerami należy włączyć inną funkcję o nazwie "Home/Work Networking". To ustawienie znajduje się również w pliku Package.appmanifest na karcie Możliwości. Dzięki temu aplikacja przychodzące i wychodzące dostęp do sieci zaufanych miejsc użytkownika, takich jak dom i praca. Przychodzące porty krytyczne są zawsze blokowane. Aby uzyskać dostęp do usług w Internecie, należy również włączyć możliwość korzystania z Internetu (klienta).  
  
### <a name="misc"></a>Różne  
 Korzystanie z następujących klas jest obsługiwane dla aplikacji ze Sklepu Windows:  
  
1. <xref:System.ServiceModel.ChannelFactory>  
  
2. <xref:System.ServiceModel.DuplexChannelFactory%601>
  
3. <xref:System.ServiceModel.CallbackBehaviorAttribute>  
  
### <a name="defining-service-contracts"></a>Definiowanie umów serwisowych  
 Zaleca się definiowanie tylko operacji asynchronicznych usługi przy użyciu wzorca asynchroniczne oparte na zadaniach. Dzięki temu aplikacje ze Sklepu Windows pozostają responsywne podczas wywoływania operacji usługi.  
  
> [!WARNING]
> Chociaż nie wyjątek zostanie zgłoszony, jeśli zdefiniujesz operację synchroniową, zdecydowanie zaleca się definiowanie tylko operacji asynchronicznych.  
  
### <a name="calling-wcf-services-from-windows-store-applications"></a>Wywoływanie usług WCF z aplikacji ze Sklepu Windows  
 Jak wspomniano wcześniej wszystkie konfiguracje muszą być wykonane w kodzie w GetBindingForEndpoint metody w klasie wygenerowanego serwera proxy. Wywołanie operacji usługi odbywa się tak samo jak wywołanie dowolnej metody asynchronicznego opartej na zadaniach, jak pokazano w poniższym urywek kodu.  
  
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
  
 Zwróć uwagę na użycie asynchroniczne słowo kluczowe na metodę podejmowania wywołania asynchroniczne i await słowa kluczowego podczas wywoływania metody asynchroniczne.  
  
## <a name="see-also"></a>Zobacz też

- [WCF w blogu aplikacji ze Sklepu Windows](https://docs.microsoft.com/archive/blogs/piyushjo/wcf-in-windows-8-metro-styled-apps-absolutely-supported)
- [Klienci i zabezpieczenia sklepu Windows WCF](https://docs.microsoft.com/archive/blogs/piyushjo/calling-a-wcf-service-from-a-metro-application-adding-security)
- [Aplikacje ze Sklepu Windows i połączenia między komputerami](https://docs.microsoft.com/archive/blogs/piyushjo/calling-a-wcf-service-from-a-metro-application-cross-machine-scenario)
- [Wywoływanie usługi WCF wdrożonej na platformie Azure z aplikacji ze Sklepu Windows](https://docs.microsoft.com/archive/blogs/piyushjo/calling-a-wcf-service-from-a-metro-application-cross-machine-scenario)
- [Programowanie zabezpieczeń WCF](../../../../docs/framework/wcf/feature-details/programming-wcf-security.md)
- [Powiązania](../../../../docs/framework/wcf/bindings.md)

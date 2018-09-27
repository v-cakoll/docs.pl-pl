---
title: Dostęp do usług WCF za pomocą aplikacji klienckiej ze Sklepu Windows
ms.date: 03/30/2017
ms.assetid: e2002ef4-5dee-4a54-9d87-03b33d35fc52
ms.openlocfilehash: a6324d5400e9fb15b3373eea4df0a15cd7c54887
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/27/2018
ms.locfileid: "47399219"
---
# <a name="accessing-wcf-services-with-a-windows-store-client-app"></a>Dostęp do usług WCF za pomocą aplikacji klienckiej ze Sklepu Windows
Windows 8 wprowadzono nowy typ aplikacji o nazwie aplikacje Windows Store. Te aplikacje są projektowane na podstawie interfejsem ekranie dotykowym. .NET framework 4.5 umożliwia aplikacji Windows Store do wywołania usługi WCF.  
  
## <a name="wcf-support-in-windows-store-applications"></a>Obsługa usług WCF w aplikacjach Windows Store  
 Podzbiór funkcji WCF jest dostępne z poziomu aplikacji Windows Store, zobacz poniższe sekcje, aby uzyskać więcej informacji.  
  
> [!IMPORTANT]
>  Użyj syndykacji WinRT API zamiast te udostępniane przez usługi WCF. Aby uzyskać więcej informacji, zobacz [API syndykacji WinRT](https://go.microsoft.com/fwlink/?LinkId=236265)  
  
> [!WARNING]
>  Aby dodać odwołanie do składnika środowiska wykonawczego Windows usługi sieci web przy użyciu Dodaj odwołanie do usługi nie jest obsługiwane.  
  
### <a name="supported-bindings"></a>Obsługiwane powiązania  
 Następujące powiązaniami WCF są obsługiwane w Windows Store aplikacji:  
  
1.  <xref:System.ServiceModel.BasicHttpBinding>  
  
2.  <xref:System.ServiceModel.NetTcpBinding>  
  
3.  <xref:System.ServiceModel.NetHttpBinding>  
  
4.  <xref:System.ServiceModel.Channels.CustomBinding>
  
 Następujące elementy powiązania są obsługiwane w programie Windows Store aplikacji  
  
1.  <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>  
  
2.  <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>  
  
3.  <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement>  
  
4.  <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>  
  
5.  <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>  
  
6.  <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
  
7.  <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
  
8.  <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
  
9. <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>  
  
 Obsługiwane są zarówno tekstowych i binarnych kodowania. Obsługiwane są wszystkie tryby transferu WCF. Aby uzyskać więcej informacji, zobacz [przesyłanie strumieniowe przesyłanie komunikatów](../../../../docs/framework/wcf/feature-details/streaming-message-transfer.md).  
  
### <a name="add-service-reference"></a>Dodaj odwołanie do usługi  
 Aby wywołać usługi WCF z aplikacji Windows Store, użyj funkcji Dodaj odwołanie do usługi Visual Studio 2012. Zauważysz kilka zmian w funkcji Dodaj odwołanie do usługi po zakończeniu w aplikacji Windows Store. Najpierw plik konfiguracji nie jest generowany. Aplikacje Windows Store nie należy używać plików konfiguracji, więc musi być skonfigurowany w kodzie. Ten kod konfiguracji można znaleźć w pliku References.cs generowane przez Dodaj odwołanie do usługi. Aby wyświetlić ten plik, koniecznie wybierz pozycję "Pokaż wszystkie pliki" w Eksploratorze rozwiązań. Plik zostanie umieszczony w odwołania do usług, a następnie Reference.svcmap węzły w projekcie. Wszystkie operacje wygenerowane dla usług WCF w aplikacji Windows Store jest asynchroniczne, za pomocą wzorca asynchronicznego opartego na zadaniach. Aby uzyskać więcej informacji, zobacz [wzorca asynchronicznego opartego na zadaniach](https://msdn.microsoft.com/magazine/ff959203.aspx).  
  
 Ponieważ konfiguracji jest teraz generowany w kodzie, wszelkie zmiany wprowadzone w pliku Reference.cs zostaną zastąpione za każdym razem, gdy odwołanie do usługi jest aktualizowana. Aby rozwiązać ten problem kodu konfiguracji zostanie wygenerowany wewnątrz metody częściowej, można zaimplementować w klasie serwera proxy klienta. Metoda częściowa jest zadeklarowana w następujący sposób:  
  
```csharp  
static partial void Configure(System.ServiceModel.Description.ServiceEndpoint serviceEndpoint,  
            System.ServiceModel.Description.ClientCredentials clientCredentials);  
```  
  
 Następnie można zaimplementować tę metodę częściową i Zmień powiązanie lub punkt końcowy w klasie klienta serwera proxy w następujący sposób:  
  
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
 Następujące serializatory są obsługiwane w aplikacjach Windows Store:  
  
1.  DataContractSerializer  
  
2.  Klasa DataContractJsonSerializer  
  
3.  Element XmlSerializer  
  
> [!WARNING]
>  XmlDictionaryWriter.Write(DateTime) teraz zapisuje obiekt daty/godziny jako ciąg.  
  
### <a name="security"></a>Zabezpieczenia  

Następujące tryby zabezpieczeń są obsługiwane w aplikacjach Windows Store:
  
1. <xref:System.ServiceModel.SecurityMode.None>  
  
2. <xref:System.ServiceModel.SecurityMode.Transport>  
  
3. <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>
  
4. <xref:System.ServiceModel.SecurityMode.Message>
  
Następujące typy poświadczeń klienta są obsługiwane w aplikacjach Windows Store:
  
1.  Brak  
  
2.  Podstawowy  
  
3.  Podsumowanie  
  
4.  Negotiate  
  
5.  NTLM  
  
6.  Windows  
  
7.  Nazwa użytkownika (zabezpieczenia komunikatów)  
  
8.  Windows (zabezpieczenia transportu)  
  
 Do uzyskania dostępu i wysyłać domyślne poświadczenia Windows przy użyciu aplikacji Windows Store, należy włączyć tę funkcję w pliku Package.appmanifest. Otwórz ten plik i wybierz kartę funkcji wybierz pozycję "Domyślne poświadczenia Windows". Umożliwia aplikacji łączenie się z zasobami w sieci intranet, które wymagają podania poświadczeń domeny.  
  
> [!IMPORTANT]
>  Aby aplikacje Windows Store, do nawiązywania połączeń między maszyny należy włączyć dostępna inna funkcja o nazwie "Strona główna/pracy sieci". To ustawienie jest również w pliku Package.appmanifest na karcie możliwości. Zaznacz pole wyboru głównej/pracy sieci. Dzięki temu aplikację, którą przychodzący i wychodzący dostęp do sieci użytkownika przez zaufanych miejsc, takich jak macierzystego i działają. Porty przychodzące krytyczne zawsze są blokowane. Aby uzyskać dostęp do usług w Internecie, należy również włączyć możliwości Internet (klient).  
  
### <a name="misc"></a>Różne  
 Użyj następujących klas jest obsługiwana dla Windows Store aplikacji:  
  
1.  <xref:System.ServiceModel.ChannelFactory>  
  
2.  <xref:System.ServiceModel.DuplexChannelFactory%601>
  
3.  <xref:System.ServiceModel.CallbackBehaviorAttribute>  
  
### <a name="defining-service-contracts"></a>Definiowanie kontraktów usług  
 Firma Microsoft zaleca tylko Definiowanie operacji asynchronicznej usługi za pomocą wzorca asynchronicznego opartego na zadaniach. Dzięki temu aplikacje Windows Store nadal odpowiadać podczas wywoływania operacji usługi.  
  
> [!WARNING]
>  Gdy żaden wyjątek zostanie zgłoszony, jeśli zdefiniujesz Operacja synchroniczna, zdecydowanie zaleca się definiować tylko operacji asynchronicznych.  
  
### <a name="calling-wcf-services-from-windows-store-applications"></a>Wywoływanie usługi WCF z aplikacji Windows Store  
 Jak wspomniano wcześniej cała konfiguracja musi odbywać się w kodzie w metodzie GetBindingForEndpoint w klasie, wygenerowany serwer proxy. Wywoływanie operacji usługi odbywa się taka sama jak wywołanie metody asynchronicznej wszelkie zadania, jak pokazano w poniższym fragmencie kodu.  
  
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
  
 Zwróć uwagę na async — słowo kluczowe dla metody, dzięki czemu wywołania asynchronicznego i słowo kluczowe await podczas wywoływania metody asynchronicznej.  
  
## <a name="see-also"></a>Zobacz też  
 [Usługi WCF w blogu aplikacje Windows Store](https://blogs.msdn.com/b/piyushjo/archive/2011/09/22/wcf-in-win8-metro-styled-apps-absolutely-supported.aspx)  
 [Klienci WCF Windows Store i zabezpieczeń](https://blogs.msdn.com/b/piyushjo/archive/2011/10/11/calling-a-wcf-service-from-a-metro-application-adding-security.aspx)  
 [Aplikacje Windows Store i wywołań między maszyny](https://blogs.msdn.com/b/piyushjo/archive/2011/10/22/calling-a-wcf-service-from-a-metro-application-cross-machine-scenario.aspx)  
 [Wywołanie usługi WCF wdrożonych na platformie Azure z aplikacji Windows Store](https://blogs.msdn.com/b/piyushjo/archive/2011/10/22/calling-a-wcf-service-from-a-metro-application-cross-machine-scenario.aspx)  
 [Programowanie zabezpieczeń WCF](../../../../docs/framework/wcf/feature-details/programming-wcf-security.md)  
 [Powiązania](../../../../docs/framework/wcf/bindings.md)

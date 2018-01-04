---
title: "Dostęp do usług WCF za pomocą aplikacji klienckiej ze Sklepu Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e2002ef4-5dee-4a54-9d87-03b33d35fc52
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: df5e05b1896ee272e286102a6c9433fad51b3c98
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="accessing-wcf-services-with-a-windows-store-client-app"></a>Dostęp do usług WCF za pomocą aplikacji klienckiej ze Sklepu Windows
Windows 8 wprowadzono nowy typ aplikacji o nazwie aplikacje ze Sklepu Windows. Te aplikacje są została zaprojektowana interfejsu ekran dotykowy. .NET framework 4.5 umożliwia aplikacji ze Sklepu Windows do wywoływania usług WCF.  
  
## <a name="wcf-support-in-windows-store-applications"></a>Obsługa usługi WCF w aplikacjach Sklepu Windows  
 Podzbiór funkcji WCF są dostępne za pośrednictwem aplikacji Sklepu Windows, zobacz następujące sekcje, aby uzyskać więcej informacji.  
  
> [!IMPORTANT]
>  Użyj zespolonego WinRT interfejsów API, zamiast te udostępniane przez usługi WCF. Aby uzyskać więcej informacji, zobacz [API zespolonego WinRT](http://go.microsoft.com/fwlink/?LinkId=236265)  
  
> [!WARNING]
>  Dodawanie odwołania do usługi sieci web do składnika środowiska wykonawczego systemu Windows przy użyciu Dodaj odwołanie do usługi nie jest obsługiwana.  
  
### <a name="supported-bindings"></a>Obsługiwane powiązania  
 W aplikacji ze Sklepu Windows są obsługiwane następujące powiązania WCF:  
  
1.  <xref:System.ServiceModel.BasicHttpBinding>  
  
2.  <xref:System.ServiceModel.NetTcpBinding>  
  
3.  <xref:System.ServiceModel.NetHttpBinding>  
  
4.  <xref:System.ServiceModel.Channels.CustomBinding>
  
 Obsługiwane są następujące elementy powiązania w aplikacji ze Sklepu Windows  
  
1.  <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>  
  
2.  <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>  
  
3.  <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement>  
  
4.  <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>  
  
5.  <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>  
  
6.  <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
  
7.  <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
  
8.  <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
  
9. <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>  
  
 Obsługiwane są kodowania binarnego i tekstu. Obsługiwane są wszystkie tryby transferu WCF. Aby uzyskać więcej informacji, zobacz [przesyłania strumieniowego transferu wiadomości](../../../../docs/framework/wcf/feature-details/streaming-message-transfer.md).  
  
### <a name="add-service-reference"></a>Dodaj odwołanie do usługi  
 Wywoływanie usługi WCF z aplikacją ze Sklepu Windows, użyj funkcji Dodaj odwołanie do usługi Visual Studio 2012. Można zauważyć drobne zmiany w funkcji Dodaj odwołanie do usługi po zakończeniu aplikacji Sklepu Windows. Najpierw plik konfiguracji nie jest generowany. Aplikacje ze Sklepu Windows nie należy używać pliki konfiguracji, dlatego musi być skonfigurowany w kodzie. Ten kod konfiguracji można znaleźć w pliku References.cs generowane przez Dodaj odwołanie do usługi. Aby wyświetlić ten plik, upewnij się, że w Eksploratorze rozwiązań wybierz opcję "Pokaż wszystkie pliki". Plik zostanie umieszczony w odwołania do usług, a następnie Reference.svcmap węzłów w projekcie. Wszystkie operacje wygenerowany dla usług WCF w ramach aplikacji Sklepu Windows będzie za pomocą wzorca asynchronicznego opartego na zadaniach asynchronicznej. Aby uzyskać więcej informacji, zobacz [wzorca asynchronicznego opartego na zadaniach](http://msdn.microsoft.com/magazine/ff959203.aspx).  
  
 Ponieważ konfiguracji jest teraz generowany w kodzie, wszystkie zmiany wprowadzone w pliku Reference.cs byłyby zastępowane każdej aktualizacji odwołania do usługi. Aby rozwiązać ten problem kodu konfiguracji zostanie wygenerowany wewnątrz metody częściowej, które można zaimplementować klasy serwera proxy klienta. Metoda częściowa jest zadeklarowany w następujący sposób:  
  
```csharp  
static partial void Configure(System.ServiceModel.Description.ServiceEndpoint serviceEndpoint,  
            System.ServiceModel.Description.ClientCredentials clientCredentials);  
```  
  
 Następnie można zaimplementować tę metodę częściowe i Zmień powiązanie lub punkt końcowy w klasie klienta serwera proxy w następujący sposób:  
  
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
 Następujące serializatorów są obsługiwane w aplikacjach Sklepu Windows:  
  
1.  DataContractSerializer  
  
2.  Klasa DataContractJsonSerializer  
  
3.  Element XmlSerializer  
  
> [!WARNING]
>  XmlDictionaryWriter.Write(DateTime) teraz zapisuje obiekt DateTime jako ciąg.  
  
### <a name="security"></a>Zabezpieczenia  
 Następujące tryby zabezpieczeń są obsługiwane w aplikacjach Sklepu Windows  
  
1.  <xref:System.ServiceModel.SecurityMode.None>  
  
2.  <xref:System.ServiceModel.SecurityMode.Transport>  
  
3.  <!--zz <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredentials> --> `System.ServiceModel.SecurityMode.TransportWithMessageCredentials`
  
4.  <!--zz <xref:System.ServiceModel.SecurityMode.TransportCredentialOnly>  --> `System.ServiceModel.SecurityMode.TransportCredentialOnly`
  
 Następujących typów poświadczeń klienta są obsługiwane w aplikacjach Sklepu Windows  
  
1.  Brak  
  
2.  Podstawowy  
  
3.  Skrót  
  
4.  Negocjowania  
  
5.  UWIERZYTELNIANIE NTLM  
  
6.  Windows  
  
7.  Nazwa użytkownika (zabezpieczenia komunikatów)  
  
8.  Systemu Windows (TLS)  
  
 Aby aplikacje ze Sklepu Windows do uzyskania dostępu i wysyłać domyślne poświadczenia systemu Windows należy włączyć tę funkcję w pliku Package.appmanifest. Otwórz ten plik i wybierz kartę możliwości i wybierz opcję "Domyślne poświadczenia systemu Windows". Umożliwia to aplikacji nawiązać połączenie zasobów intranetowych, które wymagają podania poświadczeń domeny.  
  
> [!IMPORTANT]
>  Aby aplikacje ze Sklepu Windows do połączeń między maszyny należy włączyć kolejna możliwość o nazwie "Sieć główną/pracy". To ustawienie jest również plik Package.appmanifest na karcie możliwości. Zaznacz pole wyboru sieć główną/pracy. Dzięki temu aplikacja, którą przychodzący i wychodzący dostęp do sieci użytkownika, jego zaufanych miejsc, takich jak domu lub pracy. Krytyczne portów przychodzących są zawsze blokowany. Uzyskiwanie dostępu do usług w Internecie, należy również włączyć możliwości Internet (klient).  
  
### <a name="misc"></a>Różne  
 Korzystanie z następujących klas nie jest obsługiwane dla aplikacji ze Sklepu Windows:  
  
1.  <xref:System.ServiceModel.ChannelFactory>  
  
2.  <!--zz <xref:System.ServiceModel.DuplexChannelFactory> --> `System.ServiceModel.DuplexChannelFactory`
  
3.  <xref:System.ServiceModel.CallbackBehaviorAttribute>  
  
### <a name="defining-service-contracts"></a>Definiowanie kontraktów usługi  
 Zaleca się definiowania tylko operacje asynchroniczne usługi za pomocą wzorca asynchronicznego opartego na zadaniach. Dzięki temu aplikacje ze Sklepu Windows pozostają odpowiadać podczas wywoływania operacji usługi.  
  
> [!WARNING]
>  Gdy nie zostanie wygenerowany wyjątek w przypadku definiowania Operacja synchroniczna, zdecydowanie zaleca się definiować tylko operacji asynchronicznych.  
  
### <a name="calling-wcf-services-from-windows-store-applications"></a>Wywoływanie usług WCF z aplikacji ze Sklepu Windows  
 Jak wspomniano wcześniej cała konfiguracja musi odbywać się w kod w metodzie GetBindingForEndpoint w klasie wygenerowany serwer proxy. Wywoływanie operacji usługi odbywa się taka sama jak pokazane na poniższy fragment kodu podczas wywoływania metody asynchronicznej żadnych zadań.  
  
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
  
 Zwróć uwagę na async — słowo kluczowe na metodę wprowadzania wywołanie asynchroniczne i słowo kluczowe await podczas wywoływania metody asynchronicznej.  
  
## <a name="see-also"></a>Zobacz też  
 [Usługi WCF w blogu aplikacje Sklepu Windows](http://blogs.msdn.com/b/piyushjo/archive/2011/09/22/wcf-in-win8-metro-styled-apps-absolutely-supported.aspx)  
 [Klienci WCF Sklepu Windows i zabezpieczeń](http://blogs.msdn.com/b/piyushjo/archive/2011/10/11/calling-a-wcf-service-from-a-metro-application-adding-security.aspx)  
 [Aplikacje ze Sklepu Windows i połączeń między maszyny](http://blogs.msdn.com/b/piyushjo/archive/2011/10/22/calling-a-wcf-service-from-a-metro-application-cross-machine-scenario.aspx)  
 [Wywołanie usługi WCF wdrożona na platformie Azure z aplikacji ze Sklepu Windows](http://blogs.msdn.com/b/piyushjo/archive/2011/10/22/calling-a-wcf-service-from-a-metro-application-cross-machine-scenario.aspx)  
 [Programowanie zabezpieczeń WCF](../../../../docs/framework/wcf/feature-details/programming-wcf-security.md)  
 [Powiązania](../../../../docs/framework/wcf/bindings.md)

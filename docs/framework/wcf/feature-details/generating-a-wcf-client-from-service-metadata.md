---
title: Generowanie klienta programu WCF na podstawie metadanych usługi
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 27f8f545-cc44-412a-b104-617e0781b803
caps.latest.revision: ''
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9eedf84d1dccb8bc2540aca7e6bd338b4e58326d
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/23/2018
---
# <a name="generating-a-wcf-client-from-service-metadata"></a>Generowanie klienta programu WCF na podstawie metadanych usługi
W tym temacie opisano sposób użycia różnych przełączników w Svcutil.exe do generowania klientów z dokumentów metadanych.  
  
 Dokumentów metadanych może być na trwałe magazynu lub pobierana w trybie online. Pobieranie online następuje protokołu WS-MetadataExchange lub protokołu odnajdywanie firmy Microsoft (DISCO). Svcutil.exe wystawia następujące żądania metadanych jednocześnie do pobierania metadanych:  
  
-   Żądanie usługi WS-MetadataExchange (MEX) podany adres.  
  
-   Żądanie MEX dostarczonego adresu `/mex` dołączane.  
  
-   Żądanie DISCO (przy użyciu [DiscoveryClientProtocol](http://go.microsoft.com/fwlink/?LinkId=94777) z usług sieci Web programu ASP.NET) na podany adres.  
  
 Svcutil.exe generuje klienta oparte na sieci Web Services Description Language (WSDL) lub zasad pliku otrzymał od usługi. Główna nazwa użytkownika (UPN) jest generowana przez połączenie nazwy użytkownika z "@", a następnie dodanie w pełni kwalifikowaną nazwą domeny (FQDN). Jednak dla użytkowników, którzy zarejestrowane w usłudze Active Directory, ten format jest nieprawidłowy i nazwy UPN, generowany przez narzędzie powoduje to niepowodzenie w uwierzytelnianiu Kerberos z następujący komunikat o błędzie: **próba logowania nie powiodła się.** Aby rozwiązać ten problem, Usuń ręcznie generowany przez narzędzie pliku klienta.  
  
```  
svcutil.exe [/t:code]  <metadataDocumentPath>* | <url>* | <epr>  
```  
  
## <a name="referencing-and-sharing-types"></a>Udostępnianie typów i Tworzenie odwołań  
  
|Opcja|Opis|  
|------------|-----------------|  
|**/ reference:\<ścieżka pliku >**|Typy odwołań w określonym zestawie. Podczas generowania klientów, ta opcja umożliwia Określ zestawy, które może zawierać typy, które reprezentują importowane metadane.<br /><br /> Krótka forma: `/r`|  
|**/excludeType:\<typu >**|Określa nazwę typu w pełni kwalifikowaną lub kwalifikowaną dla zestawu mają być wykluczone z typów, do którego istnieje odwołanie kontraktu.<br /><br /> Krótka forma: `/et`|  
  
## <a name="choosing-a-serializer"></a>Wybieranie serializatora  
  
|Opcja|Opis|  
|------------|-----------------|  
|**/serializer:Auto**|Automatycznie wybiera serializatora. Ta metoda korzysta `DataContract` serializatora. W przypadku niepowodzenia `XmlSerializer` jest używany.<br /><br /> Krótka forma: `/ser:Auto`|  
|**/serializer:DataContractSerializer**|Generuje typów danych, które używają `DataContract` serializatora do serializacji i deserializacji.<br /><br /> Krótka forma: `/ser:DataContractSerializer`|  
|**/serializer:XmlSerializer**|Generuje typów danych, które używają `XmlSerializer` do serializacji i deserializacji.<br /><br /> Krótka forma: `/ser:XmlSerializer`|  
|**/importXmlTypes**|Konfiguruje `DataContract` serializatora do zaimportowania z systemem innym niż`DataContract` typy jako `IXmlSerializable` typów.<br /><br /> Krótka forma: `/ixt`|  
|**/dataContractOnly**|Generuje kod dla `DataContract` tylko typy. `ServiceContract` typy są generowane.<br /><br /> Należy określić tylko metadane lokalne pliki dla tej opcji.<br /><br /> Krótka forma: `/dconly`|  
  
## <a name="choosing-a-language-for-the-client"></a>Wybieranie języka dla klienta  
  
|Opcja|Opis|  
|------------|-----------------|  
|**/Language:\<języka >**|Określa język programowania do użycia podczas generowania kodu. Podaj albo nazwę języka zarejestrowany w pliku Machine.config lub w pełni kwalifikowaną nazwę klasy, która dziedziczy <xref:System.CodeDom.Compiler.CodeDomProvider>.<br /><br /> Wartości: c#, cs, csharp, vb, vbs, visualbasic, vbscript, javascript, c ++, mc, cpp<br /><br /> Domyślne: csharp<br /><br /> Krótka forma: `/l`<br /><br /> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [Klasa CodeDomProvider](http://go.microsoft.com/fwlink/?LinkId=94778).|  
  
## <a name="choosing-a-namespace-for-the-client"></a>Wybieranie Namespace dla klienta  
  
|Opcja|Opis|  
|------------|-----------------|  
|**/ NAMESPACE:\<ciąg, ciąg >**|Określa mapowania z WSDL lub schematu XML `targetNamespace` do wspólnej przestrzeni nazw, języka środowiska uruchomieniowego (języka wspólnego CLR). Przy użyciu symbolu wieloznacznego (*) dla `targetNamespace` wszystkie mapy `targetNamespaces` bez jawnego mapowania do tej przestrzeni nazw CLR.<br /><br /> Aby upewnić się, że nazwa kontraktu komunikatu nie kolidujący z nazwą operacji, Zakwalifikuj odniesienie typu double dwukropkiem (`::`) lub upewnij się, że nazwy są unikatowe.<br /><br /> Wartość domyślna: Pochodzące z docelowej przestrzeni nazw dla dokumentu schematu `DataContracts`. Domyślna przestrzeń nazw jest używana dla wszystkich innych typów wygenerowany.<br /><br /> Krótka forma: `/n`|  
  
## <a name="choosing-a-data-binding"></a>Wybieranie powiązanie danych  
  
|Opcja|Opis|  
|------------|-----------------|  
|**/enableDataBinding**|Implementuje <xref:System.ComponentModel.INotifyPropertyChanged> interfejsu na wszystkich `DataContract` typów do włączenia możliwości wiązania danych.<br /><br /> Krótka forma: `/edb`|  
  
## <a name="generating-configuration"></a>Generowanie konfiguracji  
  
|Opcja|Opis|  
|------------|-----------------|  
|**/config:\<configFile>**|Określa nazwę pliku dla pliku konfiguracyjnego wygenerowany.<br /><br /> Domyślne: output.config|  
|**/mergeConfig**|Scala istniejący plik, zamiast zastępowanie istniejącego pliku wygenerowanego konfiguracji.|  
|**/noConfig**|Generuje pliki konfiguracji.|  
  
## <a name="see-also"></a>Zobacz też  
 [Używanie metadanych](../../../../docs/framework/wcf/feature-details/using-metadata.md)  
 [Przegląd architektury metadanych](../../../../docs/framework/wcf/feature-details/metadata-architecture-overview.md)

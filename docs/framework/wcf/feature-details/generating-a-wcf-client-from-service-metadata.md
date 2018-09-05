---
title: Generowanie klienta programu WCF na podstawie metadanych usługi
ms.date: 03/30/2017
ms.assetid: 27f8f545-cc44-412a-b104-617e0781b803
ms.openlocfilehash: 78804eb7f4139280e7d72c5a45aa0ae4cc3c2d77
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43541177"
---
# <a name="generating-a-wcf-client-from-service-metadata"></a>Generowanie klienta programu WCF na podstawie metadanych usługi
W tym temacie opisano sposób użycia różnych przełączników w Svcutil.exe do generowania klientów z dokumentów metadanych.  
  
 Dokumenty metadanych mogą znajdować się na trwałego magazynu lub pobierana w trybie online. Pobieranie online jest zgodna z protokołu WS-MetadataExchange lub protokołu odnajdowania firmy Microsoft (NAJDYWANIA). Svcutil.exe generuje następujące żądania metadanych równocześnie do pobierania metadanych:  
  
-   Żądanie usługi WS-MetadataExchange (MEX) podany adres.  
  
-   Żądanie MEX podany adres z `/mex` dołączane.  
  
-   Żądanie DISCO (przy użyciu [DiscoveryClientProtocol](https://go.microsoft.com/fwlink/?LinkId=94777) z usług sieci Web platformy ASP.NET) na podany adres.  
  
 Svcutil.exe generuje klienta oparty na sieci Web Services Description Language (WSDL) lub zasad pliku otrzymanych z usługi. Główna nazwa użytkownika (UPN) jest generowana przez połączenie nazwy użytkownika z "\@", a następnie dodając w pełni kwalifikowaną nazwą domeny (FQDN). Jednak dla użytkowników, którzy zarejestrowali się w usłudze Active Directory, ten format jest nieprawidłowy, a nazwy UPN, generowany przez narzędzie powoduje awarię w uwierzytelnianiu Kerberos z następujący komunikat o błędzie: **próba logowania nie powiodła się.** Aby rozwiązać ten problem, należy ręcznie rozwiązać pliku klienta, który wygenerował narzędzie.  
  
```  
svcutil.exe [/t:code]  <metadataDocumentPath>* | <url>* | <epr>  
```  
  
## <a name="referencing-and-sharing-types"></a>Udostępnianie typów i odwoływanie się do  
  
|Opcja|Opis|  
|------------|-----------------|  
|**/ reference:\<ścieżka pliku >**|Typy odwołań w określonym zestawie. Podczas generowania klientów Użyj tej opcji, aby określić zestawy, które mogą zawierać typy reprezentujące importowane metadane.<br /><br /> Krótka: `/r`|  
|**/excludeType:\<typ >**|Określa nazwę typu w pełni kwalifikowaną lub kwalifikowaną dla zestawu, które mają być wykluczone z typów kontraktu odwołania.<br /><br /> Krótka: `/et`|  
  
## <a name="choosing-a-serializer"></a>Wybieranie serializatora  
  
|Opcja|Opis|  
|------------|-----------------|  
|**/serializer:Auto**|Automatycznie wybiera element serializujący. Ta metoda korzysta z `DataContract` serializatora. W przypadku niepowodzenia `XmlSerializer` jest używany.<br /><br /> Krótka: `/ser:Auto`|  
|**/serializer:DataContractSerializer**|Generuje typy danych, które używają `DataContract` serializatora do serializacji i deserializacji.<br /><br /> Krótka: `/ser:DataContractSerializer`|  
|**/serializer:XmlSerializer**|Generuje typy danych, które używają `XmlSerializer` do serializacji i deserializacji.<br /><br /> Krótka: `/ser:XmlSerializer`|  
|**/importXmlTypes**|Konfiguruje `DataContract` serializatora do zaimportowania non -`DataContract` typów jako `IXmlSerializable` typów.<br /><br /> Krótka: `/ixt`|  
|**/dataContractOnly**|Generuje kod dla `DataContract` tylko typy. `ServiceContract` typy są generowane.<br /><br /> Należy określić tylko pliki lokalne metadanych dla tej opcji.<br /><br /> Krótka: `/dconly`|  
  
## <a name="choosing-a-language-for-the-client"></a>Wybór języka klienta  
  
|Opcja|Opis|  
|------------|-----------------|  
|**/Language:\<języka >**|Określa język programowania na potrzeby generowania kodu. Podaj nazwę języka zarejestrowanych w pliku Machine.config lub w pełni kwalifikowaną nazwę klasy, która dziedziczy po elemencie <xref:System.CodeDom.Compiler.CodeDomProvider>.<br /><br /> Wartości: c#, cs, csharp, vb, vbs, języka Visual Basic, vbscript, javascript, c ++, mc, cpp<br /><br /> Domyślne: csharp<br /><br /> Krótka: `/l`<br /><br /> Aby uzyskać więcej informacji, zobacz [klasy CodeDomProvider](https://go.microsoft.com/fwlink/?LinkId=94778).|  
  
## <a name="choosing-a-namespace-for-the-client"></a>Wybieranie Namespace dla klienta  
  
|Opcja|Opis|  
|------------|-----------------|  
|**/ NAMESPACE:\<string, string >**|Określa mapowanie schematu WSDL lub XML `targetNamespace` do wspólnej przestrzeni nazw środowiska języka wspólnego (CLR). Użycie symbolu wieloznacznego (*) dla `targetNamespace` mapuje wszystkie `targetNamespaces` bez jawnego mapowania na przestrzeń nazw CLR.<br /><br /> Aby upewnić się, że nazwa kontraktu komunikatu nie kolidujący z nazwą operacji, albo kwalifikowania odniesienie typu przy użyciu dwukropków double (`::`) lub upewnij się, że nazwy są unikatowe.<br /><br /> Wartość domyślna: Pochodzi z docelowej przestrzeni nazw dokumentu schematu dla `DataContracts`. Domyślny obszar nazw jest używana dla wszystkich innych wygenerowanych typów.<br /><br /> Krótka: `/n`|  
  
## <a name="choosing-a-data-binding"></a>Wybieranie powiązanie danych  
  
|Opcja|Opis|  
|------------|-----------------|  
|**/enableDataBinding**|Implementuje <xref:System.ComponentModel.INotifyPropertyChanged> interfejsu na wszystkich `DataContract` typy umożliwiające powiązanie danych.<br /><br /> Krótka: `/edb`|  
  
## <a name="generating-configuration"></a>Generowanie konfiguracji  
  
|Opcja|Opis|  
|------------|-----------------|  
|**/config:\<configFile>**|Określa nazwę pliku dla pliku wygenerowaną konfigurację.<br /><br /> Domyślne: output.config|  
|**/mergeConfig**|Scala wygenerowaną konfigurację istniejącego pliku, zamiast nadpisywać istniejący plik.|  
|**/noConfig**|Nie generują pliki konfiguracji.|  
  
## <a name="see-also"></a>Zobacz też  
 [Używanie metadanych](../../../../docs/framework/wcf/feature-details/using-metadata.md)  
 [Przegląd architektury metadanych](../../../../docs/framework/wcf/feature-details/metadata-architecture-overview.md)

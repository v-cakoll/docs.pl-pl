---
title: "Instrukcje: Skracanie czasu uruchamiania aplikacji klienckich programu WCF za pomocą elementu XmlSerializer"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 21093451-0bc3-4b1a-9a9d-05f7f71fa7d0
caps.latest.revision: "13"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3087dd479b386036d62df2ef9f792a1582d696c2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-improve-the-startup-time-of-wcf-client-applications-using-the-xmlserializer"></a>Instrukcje: Skracanie czasu uruchamiania aplikacji klienckich programu WCF za pomocą elementu XmlSerializer
Usługi i aplikacje klienckie, które używają typów danych, które są do serializacji przy użyciu <xref:System.Xml.Serialization.XmlSerializer> Generowanie i kompilacja kodu serializacji dla tych typów danych w czasie wykonywania, co może spowodować wolne uruchamiania wydajności.  
  
> [!NOTE]
>  Kod serializacji wstępnie wygenerowane można tylko w aplikacjach klienckich, a nie w usługach.  
  
 [Narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) może poprawić wydajność uruchamiania tych aplikacji przez generowania kodu serializacji niezbędne z skompilowane zestawy dla aplikacji. Svcutil.exe generuje kodu serializacji dla wszystkich typów danych używany w kontraktach usług w zestawie skompilowanej aplikacji, które można serializować przy użyciu <xref:System.Xml.Serialization.XmlSerializer>. Kontrakty usługi i działania, korzystających z <xref:System.Xml.Serialization.XmlSerializer> są oznaczone ikoną z <xref:System.ServiceModel.XmlSerializerFormatAttribute>.  
  
### <a name="to-generate-xmlserializer-serialization-code"></a>Do generowania kodu serializacji XmlSerializer  
  
1.  Kompilowanie kodu usługi lub klienta do jednego lub więcej zestawów.  
  
2.  Otwórz wiersz polecenia z zestawu SDK.  
  
3.  W wierszu polecenia Uruchom narzędzie Svcutil.exe w następującym formacie.  
  
    ```  
    svcutil.exe /t:xmlSerializer  <assemblyPath>*  
    ```  
  
     `assemblyPath` Argument określa ścieżkę do zestawu, który zawiera typy kontraktu usługi. Svcutil.exe generuje kodu serializacji dla wszystkich typów danych używany w kontraktach usług w zestawie skompilowanej aplikacji, które można serializować przy użyciu <xref:System.Xml.Serialization.XmlSerializer>.  
  
     Svcutil.exe tylko można wygenerować kodu serializacji C#. Jeden plik kod źródłowy jest generowany dla każdego zestawu wejściowego. Nie można użyć **/language** przełącznik, aby zmienić język wygenerowanego kodu.  
  
     Aby określić ścieżkę do zestawów zależnych, użyj **/reference** opcji.  
  
4.  Udostępnij serializacji wygenerowany kod aplikacji przy użyciu jednej z następujących opcji:  
  
    1.  Skompilować kodu serializacji wygenerowanego w osobny zestaw o nazwie [*oryginalnego zestawu*]. XmlSerializers.dll (na przykład MyApp.XmlSerializers.dll). Aplikacja musi być można załadować zestawu, które muszą być podpisane przy użyciu tego samego klucza oryginalnego zestawu. Skompiluj oryginalnego zestawu, musisz ponownie wygenerować zestawu serializacji.  
  
    2.  Skompilować kodu serializacji wygenerowanego w osobny zestaw i użyj <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute> umowy serwisowej, która używa <xref:System.ServiceModel.XmlSerializerFormatAttribute>. Ustaw <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.AssemblyName%2A> lub <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.CodeBase%2A> właściwości, aby wskazywał zestawu skompilowanego serializacji.  
  
    3.  Skompilować kodu serializacji wygenerowanego do używanego zestawu aplikacji i Dodaj <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute> do umowy serwisowej, która używa <xref:System.ServiceModel.XmlSerializerFormatAttribute>. Nie ustawiaj <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.AssemblyName%2A> lub <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.CodeBase%2A> właściwości. Domyślny zestaw serializacji zakłada się, że bieżący zestaw.  
  
### <a name="to-generate-xmlserializer-serialization-code-in-visual-studio"></a>Do generowania kodu serializacji XmlSerializer w programie Visual Studio  
  
1.  Tworzenie usługi WCF i klienta projektów programu Visual Studio. Następnie należy dodać odwołania do usługi do projektu klienta.  
  
2.  Dodaj <xref:System.ServiceModel.XmlSerializerFormatAttribute> w kontrakcie usługi *reference.cs* plik w projekcie aplikacji klienta, w obszarze **servicereference kierowany** -> **reference.svcmap** . Należy pamiętać, że trzeba Pokaż wszystkie pliki w **Eksploratora rozwiązań** aby te pliki.  
  
3.  Tworzenie aplikacji klienckich.  
  
4.  Użyj [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) do utworzenia wstępnie wygenerowanego serializatora *.cs* pliku za pomocą polecenia:  
  
    ```  
    svcutil.exe /t:xmlSerializer  <assemblyPath>*  
    ```  
  
     Argument zestawu assemblyPath Określa ścieżkę do zestawu klienta WCF.  
  
     Takie jak:  
  
    ```  
    svcutil.exe /t:xmlSerializer wcfclient.exe  
    ```  
  
     *WCFClient.XmlSerializers.dll.cs* zostanie utworzony plik.  
  
5.  Kompilowanie zestawu wstępnie wygenerowane serializacji.  
  
     Oparte na przykład w poprzednim kroku, kompilacji polecenie będzie następujące:  
  
    ```  
    csc /r:wcfclient.exe /out:WCFClient.XmlSerializers.dll /t:library WCFClient.XmlSerializers.dll.cs  
    ```  
  
     Sprawdź wygenerowany *WCFClient.XmlSerializers.dll* znajduje się w tym samym katalogu co aplikacja klienta, który jest *WCFClient.exe* w takim przypadku.  
  
6.  Uruchom aplikację klienta w zwykły sposób. Zestaw wstępnie wygenerowane serializacji będą używane.  
  
## <a name="example"></a>Przykład  
 Polecenie generuje typy serializacji dla `XmlSerializer` typów, które usługi umów w przypadku użycia zestawu.  
  
```  
svcutil /t:xmlserializer myContractLibrary.exe  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Narzędzie do obsługi metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)

---
title: Narzędzie klienta usługi danych WCF (DataSvcUtil.exe)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, generating client data classes
- WCF Data Services, client library
- WCF Data Services, consuming
ms.assetid: 9d0af606-929b-4c03-b307-3ef5f705afce
ms.openlocfilehash: 3206947d06a1736116674b70e469c20f8f4fca86
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33364529"
---
# <a name="wcf-data-service-client-utility-datasvcutilexe"></a>Narzędzie klienta usługi danych WCF (DataSvcUtil.exe)
DataSvcUtil.exe jest udostępniane przez narzędzie wiersza polecenia [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] która zużywa [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] źródła danych i wygeneruje klasy usługi danych klienta, które są niezbędne do uzyskania dostępu do usługi danych z aplikacją kliencką programu .NET Framework. To narzędzie można wygenerować klas danych przy użyciu następujących źródeł metadanych:  
  
-   Głównego adresu URI usługi danych. Narzędzie żądań dokumentu metadanych usługi, opisujący modelu danych udostępnianych przez usługę danych. Aby uzyskać więcej informacji, zobacz [OData: Dokument metadanych usługi](http://go.microsoft.com/fwlink/?LinkId=186070).  
  
-   Plik modelu danych (CSDL) zdefiniowany przy użyciu języka schematu koncepcyjnego definition language (CSDL), zgodnie z definicją w [ \[MC CSDL\]: koncepcyjny formatu pliku definicji schematu](http://go.microsoft.com/fwlink/?LinkID=159072) specyfikacji.  
  
-   Plik edmx utworzone przy użyciu narzędzi do modelu danych jednostki, które są dostarczane z programu Entity Framework. Aby uzyskać więcej informacji, zobacz [ \[MC EDMX\]: modelu Entity Data Model danych usługi tworzenia pakietów formatu](http://go.microsoft.com/fwlink/?LinkID=178833) specyfikacji.  
  
 Aby uzyskać więcej informacji, zobacz [porady: ręcznie wygenerować klienta usługi klas danych](../../../../docs/framework/data/wcf/how-to-manually-generate-client-data-service-classes-wcf-data-services.md).  
  
 Instalacja narzędzia DataSvcUtil.exe w [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] katalogu. W wielu przypadkach to znajduje się w C:\Windows\Microsoft.NET\Framework\v4.0. 64-bitowe systemy to znajduje się w C:\Windows\Microsoft.NET\Framework64\v4.0. Można również przejść DataSvcUtil.exe narzędzie z wiersza polecenia programu Visual Studio (kliknij **Start**, wskaż polecenie **wszystkie programy**, wskaż polecenie **programu Microsoft Visual Studio 2010**, wskaż **programu Visual Studio Tools**, a następnie kliknij przycisk **programu Visual Studio 2010 polecenie wiersza**).  
  
## <a name="syntax"></a>Składnia  
  
```  
datasvcutil /out:file [/in:file | /uri:serviceuri] [/dataservicecollection] [/language:devlang] [/nologo] [/version:ver] [/help]  
```  
  
#### <a name="parameters"></a>Parametry  
  
|Opcja|Opis|  
|------------|-----------------|  
|`/dataservicecollection`|Określa, że generowane jest również kod wymagany do powiązanie obiektów z formantami.|  
|`/help`<br /><br /> —lub—<br /><br /> `/?`|Wyświetla składnię polecenia i opcje narzędzia.|  
|`/in:` *\<Plik >*|Określa plik .csdl lub edmx lub katalog, w którym znajduje się plik.|  
|`/language:`[VB&#124;CSharp]|Określa język dla plików źródłowych wygenerowanego kodu. Wartością domyślną języka C#.|  
|`/nologo`|Pomija wyświetlanie komunikaty o prawach autorskich.|  
|`/out:` *\<Plik >*|Określa nazwę pliku kodu źródłowego, który zawiera klasy usługi danych wygenerowanego klienta.|  
|`/uri:` *\<ciąg >*|Identyfikator URI [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] źródła danych.|  
|`/version:`[1.0&#124;2.0]|Określa wersję najwyższy zaakceptowane [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]. Wersja jest określana na podstawie `DataServiceVersion` atrybutu element DataService w metadanych usługi zwracanych danych. Aby uzyskać więcej informacji, zobacz [przechowywanie wersji usługi danych](../../../../docs/framework/data/wcf/data-service-versioning-wcf-data-services.md). Po określeniu `/dataservicecollection` parametru, należy także określić `/version:2.0` do włączenia możliwości wiązania danych.|  
  
## <a name="see-also"></a>Zobacz też  
 [Generowanie biblioteki klienta usługi danych](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md)  
 [Instrukcje: Dodawanie odwołania do usługi danych](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md)

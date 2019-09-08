---
title: Narzędzie klienta usługi danych WCF (DataSvcUtil.exe)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, generating client data classes
- WCF Data Services, client library
- WCF Data Services, consuming
ms.assetid: 9d0af606-929b-4c03-b307-3ef5f705afce
ms.openlocfilehash: 97e9502176e0cc2f36d67ee3dc8e8d0739a009b2
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70790193"
---
# <a name="wcf-data-service-client-utility-datasvcutilexe"></a>Narzędzie klienta usługi danych WCF (DataSvcUtil.exe)

DataSvcUtil. exe to narzędzie wiersza polecenia zapewniane przez usługi danych programu WCF, które korzysta [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] z kanału informacyjnego i generuje klasy usługi danych klienta, które są konieczne w celu uzyskania dostępu do usługi danych z .NET Framework aplikacji klienckiej. To narzędzie może generować klasy danych przy użyciu następujących źródeł metadanych:

- Główny identyfikator URI usługi danych. Narzędzie żąda dokumentu metadanych usługi, który opisuje model danych uwidoczniony przez usługę danych. Aby uzyskać więcej informacji, [zobacz OData: Dokument](https://go.microsoft.com/fwlink/?LinkId=186070)metadanych usługi.

- Plik modelu danych (. csdl) zdefiniowany przy użyciu języka z definicją schematu koncepcyjnego (CSDL), zgodnie z definicją w [ \[pliku\]MC-CSDL: Specyfikacja formatu](https://go.microsoft.com/fwlink/?LinkID=159072) pliku definicji schematu koncepcyjnego.

- Plik. edmx utworzony przy użyciu narzędzi Entity Data Model, które są dostarczane z Entity Framework. Aby uzyskać więcej informacji, zobacz [ \[MC-edmx\]: Entity Data Model Data Services specyfikacji formatu](https://go.microsoft.com/fwlink/?LinkID=178833) pakietu.

Aby uzyskać więcej informacji, zobacz [jak: Generuj ręcznie klasy](how-to-manually-generate-client-data-service-classes-wcf-data-services.md)usługi danych klienta.

Narzędzie DataSvcUtil. exe jest instalowane w katalogu .NET Framework. W wielu przypadkach znajduje się to w *C:\Windows\Microsoft.NET\Framework\v4.0*. W przypadku systemów 64-bitowych ten program znajduje się w *C:\Windows\Microsoft.NET\Framework64\v4.0*. Możesz również uzyskać dostęp do narzędzia DataSvcUtil. exe z wiersz polecenia dla deweloperów dla programu Visual Studio.

## <a name="syntax"></a>Składnia

```
datasvcutil /out:file [/in:file | /uri:serviceuri] [/dataservicecollection] [/language:devlang] [/nologo] [/version:ver] [/help]
```

## <a name="parameters"></a>Parametry

|Opcja|Opis|
|------------|-----------------|
|`/dataservicecollection`|Określa, że jest również generowany kod wymagany do powiązania obiektów z kontrolkami.|
|`/help`<br /><br /> —lub—<br /><br /> `/?`|Wyświetla składnię polecenia i opcje narzędzia.|
|`/in:` *\<file>*|Określa plik CSDL lub edmx lub katalog, w którym znajduje się plik.|
|`/language:`[VB&#124;CSharp]|Określa język generowanych plików kodu źródłowego. Język jest wartością domyślną C#.|
|`/nologo`|Pomija wyświetlanie komunikatu o prawach autorskich.|
|`/out:` *\<file>*|Określa nazwę pliku kodu źródłowego, który zawiera wygenerowane klasy usługi danych klienta.|
|`/uri:` *ciąg\<>*|Identyfikator URI źródła danych OData.|
|`/version:`[1.0&#124;2.0]|Określa najwyższą zaakceptowaną wersję usługi OData. Wersja jest określana na podstawie `DataServiceVersion` atrybutu elementu DataService w metadanych zwracanej usługi danych. Aby uzyskać więcej informacji, zobacz [przechowywanie wersji usługi danych](data-service-versioning-wcf-data-services.md). Po określeniu `/dataservicecollection` parametru należy również określić `/version:2.0` , aby włączyć powiązanie danych.|

## <a name="see-also"></a>Zobacz także

- [Generowanie biblioteki klienta usługi danych](generating-the-data-service-client-library-wcf-data-services.md)
- [Instrukcje: Dodawanie odwołania do usługi danych](how-to-add-a-data-service-reference-wcf-data-services.md)

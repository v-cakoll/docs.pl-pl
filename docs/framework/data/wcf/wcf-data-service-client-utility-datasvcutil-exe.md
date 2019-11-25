---
title: Narzędzie klienta usługi danych WCF (DataSvcUtil.exe)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, generating client data classes
- WCF Data Services, client library
- WCF Data Services, consuming
ms.assetid: 9d0af606-929b-4c03-b307-3ef5f705afce
ms.openlocfilehash: de260e1a6b58fdbac1a2f0f40c7ec2e50b13644e
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73975083"
---
# <a name="wcf-data-service-client-utility-datasvcutilexe"></a>Narzędzie klienta usługi danych WCF (DataSvcUtil.exe)

DataSvcUtil. exe to narzędzie wiersza polecenia zapewniane przez Usługi danych programu WCF, które korzysta z kanału informacyjnego protokołu Open Data Protocol (OData) i generuje klasy usługi danych klienta, które są konieczne w celu uzyskania dostępu do usługi danych z .NET Framework aplikacji klienckiej. To narzędzie może generować klasy danych przy użyciu następujących źródeł metadanych:

- Główny identyfikator URI usługi danych. Narzędzie żąda dokumentu metadanych usługi, który opisuje model danych uwidoczniony przez usługę danych. Aby uzyskać więcej informacji, zobacz [dokument metadanych usługi OData: Service](https://go.microsoft.com/fwlink/?LinkId=186070).

- Plik modelu danych (CSDL) zdefiniowany przy użyciu języka definicji schematu koncepcyjnego (CSDL), zgodnie z definicją w [\[MC-csdl\]: specyfikacja formatu pliku definicji schematu koncepcyjnego](https://go.microsoft.com/fwlink/?LinkID=159072) .

- Plik. edmx utworzony przy użyciu narzędzi Entity Data Model, które są dostarczane z Entity Framework. Aby uzyskać więcej informacji, zobacz [\[MC-EDMX\]: Entity Data Model dla specyfikacji formatu pakietu Data Services](https://go.microsoft.com/fwlink/?LinkID=178833) .

Aby uzyskać więcej informacji, zobacz [jak: ręczne generowanie klas usługi danych klienta](how-to-manually-generate-client-data-service-classes-wcf-data-services.md).

Narzędzie DataSvcUtil. exe jest instalowane w katalogu .NET Framework. W wielu przypadkach znajduje się to w *C:\Windows\Microsoft.NET\Framework\v4.0*. W przypadku systemów 64-bitowych ten program znajduje się w *C:\Windows\Microsoft.NET\Framework64\v4.0*. Możesz również uzyskać dostęp do narzędzia DataSvcUtil. exe z wiersz polecenia dla deweloperów dla programu Visual Studio.

## <a name="syntax"></a>Składnia

```console
datasvcutil /out:file [/in:file | /uri:serviceuri] [/dataservicecollection] [/language:devlang] [/nologo] [/version:ver] [/help]
```

## <a name="parameters"></a>Parametry

|Opcja|Opis|
|------------|-----------------|
|`/dataservicecollection`|Określa, że jest również generowany kod wymagany do powiązania obiektów z kontrolkami.|
|`/help`<br /><br /> —lub—<br /><br /> `/?`|Wyświetla składnię polecenia i opcje narzędzia.|
|`/in:` *\<pliku >*|Określa plik CSDL lub edmx lub katalog, w którym znajduje się plik.|
|`/language:`[VB&#124;CSharp]|Określa język generowanych plików kodu źródłowego. Język jest wartością domyślną C#.|
|`/nologo`|Pomija wyświetlanie komunikatu o prawach autorskich.|
|`/out:` *\<pliku >*|Określa nazwę pliku kodu źródłowego, który zawiera wygenerowane klasy usługi danych klienta.|
|*ciąg\<`/uri:` >*|Identyfikator URI źródła danych OData.|
|`/version:`[1,0&#124;2,0]|Określa najwyższą zaakceptowaną wersję usługi OData. Wersja jest określana na podstawie atrybutu `DataServiceVersion` elementu DataService w metadanych zwracanej usługi danych. Aby uzyskać więcej informacji, zobacz [przechowywanie wersji usługi danych](data-service-versioning-wcf-data-services.md). Po określeniu parametru `/dataservicecollection` należy również określić `/version:2.0`, aby włączyć powiązanie danych.|

## <a name="see-also"></a>Zobacz także

- [Generowanie biblioteki klienta usługi danych](generating-the-data-service-client-library-wcf-data-services.md)
- [Instrukcje: Dodawanie odwołania do usługi danych](how-to-add-a-data-service-reference-wcf-data-services.md)

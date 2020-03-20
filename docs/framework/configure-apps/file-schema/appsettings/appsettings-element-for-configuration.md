---
title: <appSettings>, element dla <configuration>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings
helpviewer_keywords:
- appSettings Element
- <appSettings> Element
ms.assetid: 39694cc4-6b84-45a6-9329-385a0d8b48fe
ms.openlocfilehash: ea341d562f4b163a3a1771da0f20903b7d64bcdf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155534"
---
# <a name="appsettings-element-for-configuration"></a>\<appSettings> elementem \<> konfiguracyjnym

Zawiera niestandardowe ustawienia aplikacji. Jest to wstępnie zdefiniowana sekcja konfiguracji dostarczona przez program .NET Framework.

&nbsp;konfiguracji appSettings>[** \<**](../configuration-element.md) &nbsp; ** \<**

## <a name="syntax"></a>Składnia

```xml
<appSettings>
  <!-- Elements to add, clear, or remove configuration settings -->
</appSettings>
```

## <a name="attribute"></a>Atrybut

|           | Opis |
| --------- | ----------- |
| **Plik**  | Atrybut opcjonalny.<br><br>Określa względną ścieżkę do pliku zewnętrznego zawierającego niestandardowe ustawienia konfiguracji aplikacji. Określony plik zawiera ten sam rodzaj ustawień, które są określone ** \< **w ** \<>dodawania **, usuń>i ** \<wyczyść>** elementy i używa tego samego formatu pary klucz/wartość co te elementy.<br><br>Określona ścieżka jest względem głównego pliku konfiguracyjnego. W przypadku aplikacji Windows Forms jest to folder binarny (na przykład */bin/debug*), a nie lokalizacja pliku konfiguracji aplikacji. W przypadku aplikacji formularzy sieci Web ścieżka jest względem katalogu głównego aplikacji, w którym znajduje się plik *web.config.*<br><br>Środowisko wykonawcze ignoruje atrybut, jeśli nie można odnaleźć określonego pliku. |

## <a name="parent-element"></a>Element nadrzędny

|     | Opis |
| --- | ----------- |
| [** \<>konfiguracyjne** Element](../configuration-element.md) | Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework. |

## <a name="child-elements"></a>Elementy podrzędne

|     | Opis |
| --- | ----------- |
| [**\<dodaj>**](add-element-for-appsettings.md) | Dodaje niestandardowe ustawienie aplikacji. |
| [**\<wyraźne>**](clear-element-for-appsettings.md) | Czyści wszystkie wcześniej zdefiniowane ustawienia aplikacji. |
| [**\<usuń>**](remove-element-for-appsettings.md) | Usuwa uprzednio zdefiniowane ustawienie aplikacji. |

## <a name="remarks"></a>Uwagi

** \<AppSettings>** element przechowuje informacje o konfiguracji aplikacji niestandardowych, takie jak parametry połączenia bazy danych, ścieżki plików, adresy URL usługi sieci Web XML lub inne niestandardowe informacje konfiguracyjne dla aplikacji. Pary klucz/wartość określone w ** \<appSettings>** element są dostępne w <xref:System.Configuration.ConfigurationSettings> kodzie przy użyciu klasy.

Atrybutu **pliku** można użyć w ** \<appSettings>** element *web.config* i pliki konfiguracyjne aplikacji. Ten atrybut określa plik konfiguracji, który zawiera dodatkowe ustawienia lub zastępuje ustawienia określone w ** \<appSettings>** element. Atrybut **pliku** może służyć w scenariuszach tworzenia zespołu kontroli źródła, takich jak gdy użytkownik chce zastąpić ustawienia projektu określone w pliku konfiguracji aplikacji.

Pliki konfiguracyjne określone przez atrybut **pliku** muszą mieć węzeł główny ** \<appSettings>,** a nie ** \<>konfiguracji **.

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano plik ustawień aplikacji zewnętrznej *(custom.config),* który definiuje niestandardowe ustawienie aplikacji:

```xml
<?xml version="1.0" encoding="utf-8" ?>
<appSettings>
  <add key="MyCustomSetting" value="MyCustomSettingValue" />
</appSettings>
```

W poniższym przykładzie pokazano plik konfiguracji aplikacji, który zużywa ustawienie w pliku ustawień zewnętrznych i ustawia własne ustawienie aplikacji:

```xml
<configuration>
  <appSettings file="custom.config">
    <add key="ApplicationName" value="MyApplication" />
  </appSettings>
</configuration>
```

## <a name="configuration-file"></a>Plik konfiguracji

Ten element może być używany w pliku konfiguracyjnym aplikacji, pliku konfiguracyjnym komputera *(Machine.config)* i plikach *Web.config,* które nie znajdują się na poziomie katalogu aplikacji.

## <a name="see-also"></a>Zobacz też

- [Schemat pliku konfiguracyjnego programu .NET Framework](../index.md)

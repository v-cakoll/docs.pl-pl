---
title: <appSettings>, element dla <configuration>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings
helpviewer_keywords:
- appSettings Element
- <appSettings> Element
ms.assetid: 39694cc4-6b84-45a6-9329-385a0d8b48fe
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6112d87afcca8b2f54508d03d3ea4c0781d7e475
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73119268"
---
# <a name="appsettings-element-for-configuration"></a>\<appSettings > elementu \<Configuration >

Zawiera niestandardowe ustawienia aplikacji. Jest to wstępnie zdefiniowana sekcja konfiguracji udostępniona przez .NET Framework.

[ **\<> konfiguracji**](../configuration-element.md)   
&nbsp;&nbsp; **\<appSettings >**

## <a name="syntax"></a>Składnia

```xml
<appSettings>
  <!-- Elements to add, clear, or remove configuration settings -->
</appSettings>
```

## <a name="attribute"></a>Atrybut

|           | Opis |
| --------- | ----------- |
| **rozszerzeniem**  | Atrybut opcjonalny.<br><br>Określa ścieżkę względną do pliku zewnętrznego zawierającego niestandardowe ustawienia konfiguracji aplikacji. Określony plik zawiera ten sam rodzaj ustawień, które są określone w **\<dodaj >** , **\<usuń >** i **\<Wyczyść elementy >** i używa tego samego formatu pary klucz/wartość, co te elementy.<br><br>Określona ścieżka jest względna w stosunku do głównego pliku konfiguracji. W przypadku aplikacji Windows Forms jest to folder binarny (na przykład */bin/debug*), a nie lokalizacja pliku konfiguracji aplikacji. W przypadku aplikacji formularzy sieci Web ścieżka jest określana względem katalogu głównego aplikacji, w którym znajduje się plik *Web. config* .<br><br>Należy pamiętać, że środowisko uruchomieniowe ignoruje atrybut, jeśli nie można znaleźć określonego pliku. |

## <a name="parent-element"></a>Element nadrzędny

|     | Opis |
| --- | ----------- |
| [ **> konfiguracji\<** Postaci](../configuration-element.md) | Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework. |

## <a name="child-elements"></a>Elementy podrzędne

|     | Opis |
| --- | ----------- |
| [ **\<Dodaj >** ](add-element-for-appsettings.md) | Dodaje niestandardowe ustawienie aplikacji. |
| [ **\<Wyczyść >** ](clear-element-for-appsettings.md) | Czyści wszystkie wcześniej zdefiniowane ustawienia aplikacji. |
| [ **\<Usuń >** ](remove-element-for-appsettings.md) | Usuwa poprzednio zdefiniowane ustawienie aplikacji. |

## <a name="remarks"></a>Uwagi

**\<appSettings >** element przechowuje niestandardowe informacje o konfiguracji aplikacji, takie jak parametry połączenia bazy danych, ścieżki plików, adresy URL usług sieci Web XML lub inne niestandardowe informacje o konfiguracji dla aplikacji. Pary klucz/wartość określone w **\<AppSettings elementu >** są dostępne w kodzie przy użyciu klasy <xref:System.Configuration.ConfigurationSettings>.

Można użyć atrybutu **pliku** w **\<AppSettings >** elementu pliku *Web. config* i plików konfiguracji aplikacji. Ten atrybut określa plik konfiguracji, który zawiera dodatkowe ustawienia lub zastępuje ustawienia określone w **\<appSettings >** elementu. Atrybut **pliku** może być używany w scenariuszach tworzenia zespołu kontroli źródła, na przykład gdy użytkownik chce zastąpić ustawienia projektu określone w pliku konfiguracyjnym aplikacji.

Pliki konfiguracyjne określone przez atrybut **pliku** muszą mieć węzeł główny **\<appSettings >** zamiast **\<> konfiguracji**.

## <a name="example"></a>Przykład

W poniższym przykładzie przedstawiono zewnętrzny plik ustawień aplikacji (*Custom. config*) definiujący niestandardowe ustawienie aplikacji:

```xml
<?xml version="1.0" encoding="utf-8" ?>
<appSettings>
  <add key="MyCustomSetting" value="MyCustomSettingValue" />
</appSettings>
```

Poniższy przykład przedstawia plik konfiguracji aplikacji, który używa ustawienia w pliku ustawień zewnętrznych i ustawia własne ustawienie aplikacji:

```xml
<configuration>
  <appSettings file="custom.config">
    <add key="ApplicationName" value="MyApplication" />
  </appSettings>
</configuration>
```

## <a name="configuration-file"></a>Plik konfiguracji

Tego elementu można użyć w pliku konfiguracyjnym aplikacji, pliku konfiguracji komputera (*Machine. config*) i plikach *Web. config* , które nie znajdują się na poziomie katalogu aplikacji.

## <a name="see-also"></a>Zobacz także

- [Schemat pliku konfiguracji dla .NET Framework](../index.md)

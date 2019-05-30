---
title: <remove> element dla NameValueSectionHandler i DictionarySectionHandler
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: 8d8af7f5-26c9-4db9-bbe4-b2a4e6949568
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: 062aa3921d29cffd33db2d96096ef25c2b819030
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66300697"
---
# <a name="remove-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a><span data-ttu-id="d0dd0-102">\<Usuń >, element dla NameValueSectionHandler i DictionarySectionHandler</span><span class="sxs-lookup"><span data-stu-id="d0dd0-102">\<remove> element for NameValueSectionHandler and DictionarySectionHandler</span></span>

<span data-ttu-id="d0dd0-103">Usuwa ustawienie uprzednio zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="d0dd0-103">Removes a previously defined setting.</span></span>

<span data-ttu-id="d0dd0-104">[ **\<Konfiguracja >** ](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="d0dd0-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="d0dd0-105">&nbsp;&nbsp;[ **\<sectionName>** ](~/docs/framework/configure-apps/file-schema/custom-element-2.md) </span><span class="sxs-lookup"><span data-stu-id="d0dd0-105">&nbsp;&nbsp;[**\<sectionName>**](~/docs/framework/configure-apps/file-schema/custom-element-2.md) </span></span>  
<span data-ttu-id="d0dd0-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<remove>**</span><span class="sxs-lookup"><span data-stu-id="d0dd0-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>

## <a name="syntax"></a><span data-ttu-id="d0dd0-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="d0dd0-107">Syntax</span></span>

```xml
<add remove="key" />
```

## <a name="attribute"></a><span data-ttu-id="d0dd0-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="d0dd0-108">Attribute</span></span>

|           | <span data-ttu-id="d0dd0-109">Opis</span><span class="sxs-lookup"><span data-stu-id="d0dd0-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="d0dd0-110">**Klucz**</span><span class="sxs-lookup"><span data-stu-id="d0dd0-110">**key**</span></span>   | <span data-ttu-id="d0dd0-111">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="d0dd0-111">Required attribute.</span></span><br><br><span data-ttu-id="d0dd0-112">Określa nazwę ustawienie, aby usunąć.</span><span class="sxs-lookup"><span data-stu-id="d0dd0-112">Specifies the name of the setting to remove.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="d0dd0-113">Element nadrzędny</span><span class="sxs-lookup"><span data-stu-id="d0dd0-113">Parent element</span></span>

| <span data-ttu-id="d0dd0-114">Element</span><span class="sxs-lookup"><span data-stu-id="d0dd0-114">Element</span></span> | <span data-ttu-id="d0dd0-115">Opis</span><span class="sxs-lookup"><span data-stu-id="d0dd0-115">Description</span></span> |
| ------- | ------------|
| [<span data-ttu-id="d0dd0-116"> *\*\<parametrami sectionName >** — Element</span><span class="sxs-lookup"><span data-stu-id="d0dd0-116">**\<sectionName>** Element</span></span>](~/docs/framework/configure-apps/file-schema/custom-element-2.md) | <span data-ttu-id="d0dd0-117">Definiuje ustawienia powiązane z sekcji konfiguracji niestandardowej, korzystających z <xref:System.Configuration.NameValueSectionHandler> i <xref:System.Configuration.DictionarySectionHandler> klasy.</span><span class="sxs-lookup"><span data-stu-id="d0dd0-117">Defines settings for custom configuration sections that use the <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler> classes.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="d0dd0-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="d0dd0-118">Child elements</span></span>

<span data-ttu-id="d0dd0-119">Brak</span><span class="sxs-lookup"><span data-stu-id="d0dd0-119">None</span></span>

## <a name="remarks"></a><span data-ttu-id="d0dd0-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d0dd0-120">Remarks</span></span>

<span data-ttu-id="d0dd0-121">Możesz użyć  **\<Usuń >** elementu do usunięcia ustawień z poziomu aplikacji, które zostały zdefiniowane na wyższym poziomie w hierarchii plików konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="d0dd0-121">You can use the **\<remove>** element to remove settings from your application that were defined at a higher level in the configuration file hierarchy.</span></span>

## <a name="example"></a><span data-ttu-id="d0dd0-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="d0dd0-122">Example</span></span>

<span data-ttu-id="d0dd0-123">Poniższy przykład pokazuje, jak używać  **\<Usuń >** elementu w pliku konfiguracyjnym aplikacji, aby usunąć ustawienia wcześniej zdefiniowane w pliku konfiguracji komputera.</span><span class="sxs-lookup"><span data-stu-id="d0dd0-123">The following example shows how to use the **\<remove>** element in an application configuration file to remove settings previously defined in the machine configuration file.</span></span>

<span data-ttu-id="d0dd0-124">Poniższy kod pliku konfiguracji maszyny deklaruje sekcji  **\<mySection >** i dodaje dwa ustawienia `key1` i `key2`, do niego:</span><span class="sxs-lookup"><span data-stu-id="d0dd0-124">The following machine configuration file code declares the section **\<mySection>** and adds two settings, `key1` and `key2`, to it:</span></span>

```xml
<!-- Machine.config file -->
<configuration>
  <configSections>
    <section name="mySection" type="System.Configuration.NameValueSectionHandler,System" />
  </configSections>
  <mySection>
    <add key="key1" value="value1" />
    <add key="key2" value="value2" />
  </mySection>
</configuration>
```

<span data-ttu-id="d0dd0-125">Poniższy kod pliku konfiguracji aplikacji usuwa `key2` z  **\<mySection >** :</span><span class="sxs-lookup"><span data-stu-id="d0dd0-125">The following application configuration file code removes the `key2` setting from **\<mySection>**:</span></span>

```xml
<!--Application configuration file -->
<configuration>
  <mySection>
    <remove key="key2" />
  </mySection>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="d0dd0-126">Plik konfiguracji</span><span class="sxs-lookup"><span data-stu-id="d0dd0-126">Configuration file</span></span>

<span data-ttu-id="d0dd0-127">Ten element może być użyty w pliku konfiguracyjnym aplikacji, plik konfiguracji komputera (*Machine.config*), a *Web.config* pliki, które nie są na poziomie katalogu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d0dd0-127">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="d0dd0-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d0dd0-128">See also</span></span>

- [<span data-ttu-id="d0dd0-129">Schemat pliku konfiguracji dla programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="d0dd0-129">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)

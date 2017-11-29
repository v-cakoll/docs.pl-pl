---
title: "&lt;Konfiguracja&gt; — element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration
helpviewer_keywords:
- <configuration> element
- configuration element
- container tags, <configuration> element
ms.assetid: 2ec1c9dc-2e5c-4ef0-9958-81670ab88449
caps.latest.revision: "15"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 2241f3e835defe308b94d0cbad96020518dfd19b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="configuration-element"></a><span data-ttu-id="2dbdc-102">\<Konfiguracja > — element</span><span class="sxs-lookup"><span data-stu-id="2dbdc-102">\<configuration> element</span></span>

<span data-ttu-id="2dbdc-103">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2dbdc-103">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>

<span data-ttu-id="2dbdc-104">**\<Konfiguracja >**</span><span class="sxs-lookup"><span data-stu-id="2dbdc-104">**\<configuration>**</span></span>

## <a name="syntax"></a><span data-ttu-id="2dbdc-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="2dbdc-105">Syntax</span></span>

```xml
<configuration>
  <!-- Configuration settings -->
</configuration>
```

## <a name="attributes"></a><span data-ttu-id="2dbdc-106">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="2dbdc-106">Attributes</span></span>

<span data-ttu-id="2dbdc-107">Brak</span><span class="sxs-lookup"><span data-stu-id="2dbdc-107">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="2dbdc-108">Element nadrzędny</span><span class="sxs-lookup"><span data-stu-id="2dbdc-108">Parent element</span></span>

<span data-ttu-id="2dbdc-109">Brak</span><span class="sxs-lookup"><span data-stu-id="2dbdc-109">None</span></span>

## <a name="child-elements"></a><span data-ttu-id="2dbdc-110">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="2dbdc-110">Child elements</span></span>

|     | <span data-ttu-id="2dbdc-111">Opis</span><span class="sxs-lookup"><span data-stu-id="2dbdc-111">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="2dbdc-112">**\<assemblybinding — >**</span><span class="sxs-lookup"><span data-stu-id="2dbdc-112">**\<assemblyBinding>**</span></span>](~/docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md) | <span data-ttu-id="2dbdc-113">Określa zestaw powiązania zasad na poziomie konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="2dbdc-113">Specifies assembly binding policy at the configuration level.</span></span>|
| [<span data-ttu-id="2dbdc-114">**\<Uruchamianie >** schemat ustawień</span><span class="sxs-lookup"><span data-stu-id="2dbdc-114">**\<startup>** Settings Schema</span></span>](~/docs/framework/configure-apps/file-schema/startup/index.md) | <span data-ttu-id="2dbdc-115">Wszystkie elementy w schemat ustawień uruchamiania.</span><span class="sxs-lookup"><span data-stu-id="2dbdc-115">All elements in the startup settings schema.</span></span> |
| [<span data-ttu-id="2dbdc-116">**\<środowisko uruchomieniowe >** schemat ustawień</span><span class="sxs-lookup"><span data-stu-id="2dbdc-116">**\<runtime>** Settings Schema</span></span>](~/docs/framework/configure-apps/file-schema/runtime/index.md) | <span data-ttu-id="2dbdc-117">Wszystkie elementy w schemat ustawień środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="2dbdc-117">All elements in the runtime settings schema.</span></span> |
| [<span data-ttu-id="2dbdc-118">**\<System.Runtime.Remoting >** schemat ustawień</span><span class="sxs-lookup"><span data-stu-id="2dbdc-118">**\<system.runtime.remoting>** Settings Schema</span></span>](http://msdn.microsoft.com/dc2d1e62-9af7-4ca1-99fd-98b93bb4db9e) | <span data-ttu-id="2dbdc-119">Wszystkie elementy w schemacie ustawień komunikacji zdalnej.</span><span class="sxs-lookup"><span data-stu-id="2dbdc-119">All elements in the remoting settings schema.</span></span> |
| [<span data-ttu-id="2dbdc-120">**\<system.Net >** schemat ustawień</span><span class="sxs-lookup"><span data-stu-id="2dbdc-120">**\<system.Net>** Settings Schema</span></span>](~/docs/framework/configure-apps/file-schema/network/index.md) | <span data-ttu-id="2dbdc-121">Wszystkie elementy w schemacie ustawień sieci.</span><span class="sxs-lookup"><span data-stu-id="2dbdc-121">All elements in the network settings schema.</span></span> |
| [<span data-ttu-id="2dbdc-122">**\<cryptographysettings — >** schemat ustawień</span><span class="sxs-lookup"><span data-stu-id="2dbdc-122">**\<cryptographySettings>** Settings Schema</span></span>](~/docs/framework/configure-apps/file-schema/cryptography/index.md) | <span data-ttu-id="2dbdc-123">Wszystkie elementy w schemacie ustawień kryptograficznych.</span><span class="sxs-lookup"><span data-stu-id="2dbdc-123">All elements in the crypto settings schema.</span></span> |
| [<span data-ttu-id="2dbdc-124">**\<Konfiguracja >** schemat sekcji</span><span class="sxs-lookup"><span data-stu-id="2dbdc-124">**\<configuration>** Sections Schema</span></span>](~/docs/framework/configure-apps/file-schema/configuration-sections-schema.md) | <span data-ttu-id="2dbdc-125">Wszystkie elementy w schemacie ustawienia w sekcji konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="2dbdc-125">All elements in the configuration section settings schema.</span></span> |
| [<span data-ttu-id="2dbdc-126">Schemat ustawień debugowania i śledzenia</span><span class="sxs-lookup"><span data-stu-id="2dbdc-126">Trace and Debug Settings Schema</span></span>](~/docs/framework/configure-apps/file-schema/trace-debug/index.md) | <span data-ttu-id="2dbdc-127">Wszystkie elementy w schemacie ustawienia śledzenia i debugowania.</span><span class="sxs-lookup"><span data-stu-id="2dbdc-127">All elements in the trace and debug settings schema.</span></span> |
| <span data-ttu-id="2dbdc-128">[Schemat ustawień konfiguracji programu ASP.NET](https://msdn.microsoft.com/library/b5ysx397(v=vs.100).aspx)</span><span class="sxs-lookup"><span data-stu-id="2dbdc-128">[ASP.NET Configuration Settings Schema](https://msdn.microsoft.com/library/b5ysx397(v=vs.100).aspx)</span></span> | <span data-ttu-id="2dbdc-129">Wszystkie elementy w schemacie konfiguracji ASP.NET zawiera elementy dotyczące konfigurowania witryny sieci Web ASP.NET i aplikacji.</span><span class="sxs-lookup"><span data-stu-id="2dbdc-129">All elements in the ASP.NET configuration schema, which includes elements for configuring ASP.NET Web sites and applications.</span></span> <span data-ttu-id="2dbdc-130">Używane w *Web.config* plików.</span><span class="sxs-lookup"><span data-stu-id="2dbdc-130">Used in *Web.config* files.</span></span> |
| [<span data-ttu-id="2dbdc-131">**\<< webServices >** schemat ustawień</span><span class="sxs-lookup"><span data-stu-id="2dbdc-131">**\<webServices>** Settings Schema</span></span>](http://msdn.microsoft.com/f84d6d55-1add-4eb7-ae46-33df5833ea2e) | <span data-ttu-id="2dbdc-132">Wszystkie elementy w schemacie ustawienia usług sieci Web.</span><span class="sxs-lookup"><span data-stu-id="2dbdc-132">All elements in the Web services settings schema.</span></span> |
| [<span data-ttu-id="2dbdc-133">Schemat ustawień sieci Web</span><span class="sxs-lookup"><span data-stu-id="2dbdc-133">Web Settings Schema</span></span>](~/docs/framework/configure-apps/file-schema/web/index.md) | <span data-ttu-id="2dbdc-134">Wszystkie elementy w schemat ustawień sieci Web, który zawiera elementy dotyczące konfigurowania, jak działa ASP.NET przy użyciu aplikacji hosta, takich jak IIS.</span><span class="sxs-lookup"><span data-stu-id="2dbdc-134">All elements in the Web settings schema, which includes elements for configuring how ASP.NET works with a host application such as IIS.</span></span> <span data-ttu-id="2dbdc-135">Używane w *konfigurację aspnet.config* plików.</span><span class="sxs-lookup"><span data-stu-id="2dbdc-135">Used in *aspnet.config* files.</span></span> |

## <a name="remarks"></a><span data-ttu-id="2dbdc-136">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2dbdc-136">Remarks</span></span>

<span data-ttu-id="2dbdc-137">Każdy plik konfiguracyjny musi zawierać dokładnie jeden  **\<konfiguracji >** elementu.</span><span class="sxs-lookup"><span data-stu-id="2dbdc-137">Each configuration file must contain exactly one **\<configuration>** element.</span></span>

## <a name="see-also"></a><span data-ttu-id="2dbdc-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2dbdc-138">See also</span></span>

[<span data-ttu-id="2dbdc-139">Schemat pliku konfiguracji dla programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="2dbdc-139">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)

---
title: Zmiany w bibliotece klas podstawowych
description: Wyświetla listę przełomowych zmian w podstawowych bibliotekach .NET.
ms.date: 09/20/2019
ms.openlocfilehash: 8cf90ca2bc8736101c1cb8d327a93d100148937b
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021831"
---
# <a name="core-net-libraries-breaking-changes"></a><span data-ttu-id="9faea-103">Podstawowe biblioteki .NET przełamują zmiany</span><span class="sxs-lookup"><span data-stu-id="9faea-103">Core .NET libraries breaking changes</span></span>

<span data-ttu-id="9faea-104">Podstawowe biblioteki .NET zapewniają podstawowe i inne typy ogólne używane przez program .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9faea-104">The core .NET libraries provide the primitives and other general types used by .NET Core.</span></span>

<span data-ttu-id="9faea-105">Na tej stronie są udokumentowane następujące zmiany podziału:</span><span class="sxs-lookup"><span data-stu-id="9faea-105">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="9faea-106">Przełomowa zmiana</span><span class="sxs-lookup"><span data-stu-id="9faea-106">Breaking change</span></span> | <span data-ttu-id="9faea-107">Wprowadzono wersję</span><span class="sxs-lookup"><span data-stu-id="9faea-107">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="9faea-108">Interfejsy API, które zgłaszają wersję raportu, teraz zgłaszają produkt, a nie wersję pliku</span><span class="sxs-lookup"><span data-stu-id="9faea-108">APIs that report version now report product and not file version</span></span>](#apis-that-report-version-now-report-product-and-not-file-version) | <span data-ttu-id="9faea-109">3.0</span><span class="sxs-lookup"><span data-stu-id="9faea-109">3.0</span></span> |
| [<span data-ttu-id="9faea-110">Niestandardowe enkoderFallbackBuffer wystąpienia nie mogą cofać się rekursywnie</span><span class="sxs-lookup"><span data-stu-id="9faea-110">Custom EncoderFallbackBuffer instances cannot fall back recursively</span></span>](#custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively) | <span data-ttu-id="9faea-111">3.0</span><span class="sxs-lookup"><span data-stu-id="9faea-111">3.0</span></span> |
| [<span data-ttu-id="9faea-112">Zmiany zachowania formatowania zmiennoprzecinkowej i analizy</span><span class="sxs-lookup"><span data-stu-id="9faea-112">Floating point formatting and parsing behavior changes</span></span>](#floating-point-formatting-and-parsing-behavior-changed) | <span data-ttu-id="9faea-113">3.0</span><span class="sxs-lookup"><span data-stu-id="9faea-113">3.0</span></span> |
| [<span data-ttu-id="9faea-114">Operacje analizowania zmiennoprzecinkowego nie są już nieudane lub nie mogą paść za przepełnienie</span><span class="sxs-lookup"><span data-stu-id="9faea-114">Floating-point parsing operations no longer fail or throw an OverflowException</span></span>](#floating-point-parsing-operations-no-longer-fail-or-throw-an-overflowexception) | <span data-ttu-id="9faea-115">3.0</span><span class="sxs-lookup"><span data-stu-id="9faea-115">3.0</span></span> |
| [<span data-ttu-id="9faea-116">InvalidAsynchronousStateException przeniesiono do innego zestawu</span><span class="sxs-lookup"><span data-stu-id="9faea-116">InvalidAsynchronousStateException moved to another assembly</span></span>](#invalidasynchronousstateexception-moved-to-another-assembly) | <span data-ttu-id="9faea-117">3.0</span><span class="sxs-lookup"><span data-stu-id="9faea-117">3.0</span></span> |
| [<span data-ttu-id="9faea-118">NET Core 3.0 stosuje najlepsze rozwiązania unicode podczas zastępowania źle sformułowanych sekwencji bajtów UTF-8</span><span class="sxs-lookup"><span data-stu-id="9faea-118">NET Core 3.0 follows Unicode best practices when replacing ill-formed UTF-8 byte sequences</span></span>](#net-core-30-follows-unicode-best-practices-when-replacing-ill-formed-utf-8-byte-sequences) | <span data-ttu-id="9faea-119">3.0</span><span class="sxs-lookup"><span data-stu-id="9faea-119">3.0</span></span> |
| [<span data-ttu-id="9faea-120">TypeDescriptionProviderAttribute przeniesiono do innego zestawu</span><span class="sxs-lookup"><span data-stu-id="9faea-120">TypeDescriptionProviderAttribute moved to another assembly</span></span>](#typedescriptionproviderattribute-moved-to-another-assembly) | <span data-ttu-id="9faea-121">3.0</span><span class="sxs-lookup"><span data-stu-id="9faea-121">3.0</span></span> |
| [<span data-ttu-id="9faea-122">ZipArchiveEntry nie obsługuje już archiwów o niespójnych rozmiarach wpisów</span><span class="sxs-lookup"><span data-stu-id="9faea-122">ZipArchiveEntry no longer handles archives with inconsistent entry sizes</span></span>](#ziparchiveentry-no-longer-handles-archives-with-inconsistent-entry-sizes) | <span data-ttu-id="9faea-123">3.0</span><span class="sxs-lookup"><span data-stu-id="9faea-123">3.0</span></span> |
| [<span data-ttu-id="9faea-124">Typ wyjątku serializatora JSON zmieniono z JsonException na NotSupportedException</span><span class="sxs-lookup"><span data-stu-id="9faea-124">JSON serializer exception type changed from JsonException to NotSupportedException</span></span>](#json-serializer-exception-type-changed-from-jsonexception-to-notsupportedexception) | <span data-ttu-id="9faea-125">3.0</span><span class="sxs-lookup"><span data-stu-id="9faea-125">3.0</span></span> |
| [<span data-ttu-id="9faea-126">Zmiana semantyki (string)null w Utf8JsonWriter</span><span class="sxs-lookup"><span data-stu-id="9faea-126">Change in semantics of (string)null in Utf8JsonWriter</span></span>](#change-in-semantics-of-stringnull-in-utf8jsonwriter) | <span data-ttu-id="9faea-127">3.0</span><span class="sxs-lookup"><span data-stu-id="9faea-127">3.0</span></span> |
| [<span data-ttu-id="9faea-128">Metody JsonEncodedText.Encode mają dodatkowy argument JavaScriptEncoder</span><span class="sxs-lookup"><span data-stu-id="9faea-128">JsonEncodedText.Encode methods have an additional JavaScriptEncoder argument</span></span>](#jsonencodedtextencode-methods-have-an-additional-javascriptencoder-argument) | <span data-ttu-id="9faea-129">3.0</span><span class="sxs-lookup"><span data-stu-id="9faea-129">3.0</span></span> |
| [<span data-ttu-id="9faea-130">JsonFactoryConverter.CreateSeksorwerer zmieniony</span><span class="sxs-lookup"><span data-stu-id="9faea-130">JsonFactoryConverter.CreateConverter signature changed</span></span>](#jsonfactoryconvertercreateconverter-signature-changed) | <span data-ttu-id="9faea-131">3.0</span><span class="sxs-lookup"><span data-stu-id="9faea-131">3.0</span></span> |
| [<span data-ttu-id="9faea-132">Zmiany interfejsu API JsonElement</span><span class="sxs-lookup"><span data-stu-id="9faea-132">JsonElement API changes</span></span>](#jsonelement-api-changes) | <span data-ttu-id="9faea-133">3.0</span><span class="sxs-lookup"><span data-stu-id="9faea-133">3.0</span></span> |
| [<span data-ttu-id="9faea-134">FieldInfo.SetValue zgłasza wyjątek dla pól statycznych, tylko init</span><span class="sxs-lookup"><span data-stu-id="9faea-134">FieldInfo.SetValue throws exception for static, init-only fields</span></span>](#fieldinfosetvalue-throws-exception-for-static-init-only-fields) | <span data-ttu-id="9faea-135">3.0</span><span class="sxs-lookup"><span data-stu-id="9faea-135">3.0</span></span> |
| [<span data-ttu-id="9faea-136">Pola prywatne dodane do wbudowanych typów obiektów</span><span class="sxs-lookup"><span data-stu-id="9faea-136">Private fields added to built-in struct types</span></span>](#private-fields-added-to-built-in-struct-types) | <span data-ttu-id="9faea-137">2.1</span><span class="sxs-lookup"><span data-stu-id="9faea-137">2.1</span></span> |
| [<span data-ttu-id="9faea-138">Zmiana wartości domyślnej UseShellExecute</span><span class="sxs-lookup"><span data-stu-id="9faea-138">Change in default value of UseShellExecute</span></span>](#change-in-default-value-of-useshellexecute) | <span data-ttu-id="9faea-139">2.1</span><span class="sxs-lookup"><span data-stu-id="9faea-139">2.1</span></span> |
| [<span data-ttu-id="9faea-140">Wersje OpenSSL w systemie macOS</span><span class="sxs-lookup"><span data-stu-id="9faea-140">OpenSSL versions on macOS</span></span>](#openssl-versions-on-macos) | <span data-ttu-id="9faea-141">2.1</span><span class="sxs-lookup"><span data-stu-id="9faea-141">2.1</span></span> |
| [<span data-ttu-id="9faea-142">NieautoryzowaneaccessException generowane przez FileSystemInfo.Attributes</span><span class="sxs-lookup"><span data-stu-id="9faea-142">UnauthorizedAccessException thrown by FileSystemInfo.Attributes</span></span>](#unauthorizedaccessexception-thrown-by-filesysteminfoattributes) | <span data-ttu-id="9faea-143">1.0</span><span class="sxs-lookup"><span data-stu-id="9faea-143">1.0</span></span> |

## <a name="net-core-30"></a><span data-ttu-id="9faea-144">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="9faea-144">.NET Core 3.0</span></span>

[!INCLUDE[APIs that report version now report product and not file version](~/includes/core-changes/corefx/3.0/version-information-changes.md)]

***

[!INCLUDE[Custom EncoderFallbackBuffer instances cannot fall back recursively](~/includes/core-changes/corefx/3.0/custom-encoderfallbackbuffer-cannot-be-recursive.md)]

***

[!INCLUDE[Floating point formatting and parsing behavior changes](~/includes/core-changes/corefx/3.0/floating-point-changes.md)]

***

[!INCLUDE[Floating-point parsing operations no longer fail or throw an OverflowException](~/includes/core-changes/corefx/3.0/floating-point-parsing-does-not-overflow.md)]

***

[!INCLUDE[InvalidAsynchronousStateException moved to another assembly](~/includes/core-changes/corefx/3.0/move-invalidasynchronousstateexception.md)]

***

[!INCLUDE[NET Core 3.0 follows Unicode best practices when replacing ill-formed UTF-8 byte sequences](~/includes/core-changes/corefx/3.0/net-core-3-0-follows-unicode-utf8-best-practices.md)]

***

[!INCLUDE[TypeDescriptionProviderAttribute moved to another assembly](~/includes/core-changes/corefx/3.0/move-typedescriptionproviderattribute.md)]

***

[!INCLUDE[ZipArchiveEntry no longer handles archives with inconsistent entry sizes](~/includes/core-changes/corefx/3.0/ziparchiveentry-and-inconsistent-entry-sizes.md)]

***

[!INCLUDE[JSON serializer exception type changed from JsonException to NotSupportedException](~/includes/core-changes/corefx/3.0/serializer-throws-notsupportedexception.md)]

***

[!INCLUDE[Change in semantics of (string)null in Utf8JsonWriter](~/includes/core-changes/corefx/3.0/change-in-null-in-utf8jsonwriter.md)]

***

[!INCLUDE[JsonEncodedText.Encode methods have an additional JavaScriptEncoder argument](~/includes/core-changes/corefx/3.0/jsonencodedtext-encode-has-additional-argument.md)]

***

[!INCLUDE[JsonFactoryConverter.CreateConverter signature changed](~/includes/core-changes/corefx/3.0/jsonfactoryconverter-createconverter.md)]

***

[!INCLUDE[JsonElement API changes](~/includes/core-changes/corefx/3.0/jsonelement-api-changes.md)]

***

[!INCLUDE [FieldInfo.SetValue throws exception for static, init-only fields](~/includes/core-changes/corefx/3.0/fieldinfo-setvalue-exception.md)]

***

## <a name="net-core-21"></a><span data-ttu-id="9faea-145">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="9faea-145">.NET Core 2.1</span></span>

[!INCLUDE[Private fields added to built-in struct types](~/includes/core-changes/corefx/2.1/instantiate-struct.md)]

***

[!INCLUDE[Change in default value of UseShellExecute](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

***

[!INCLUDE [OpenSSL versions on macOS](../../../includes/core-changes/corefx/openssl-dependencies-macos.md)]

***

## <a name="net-core-10"></a><span data-ttu-id="9faea-146">.NET Rdzeń 1.0</span><span class="sxs-lookup"><span data-stu-id="9faea-146">.NET Core 1.0</span></span>

[!INCLUDE [UnauthorizedAccessException thrown by FileSystemInfo.Attributes](~/includes/core-changes/corefx/1.0/filesysteminfo-attributes-exceptions.md)]

***

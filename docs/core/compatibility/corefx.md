---
title: Podstawowe zmiany w bibliotece klas podstawowych
description: Wyświetla istotne zmiany w podstawowych bibliotekach programu .NET.
ms.date: 09/20/2019
ms.openlocfilehash: bc80f27a8a98890a93ad3b99e09ea7ea380d506c
ms.sourcegitcommit: c2c1269a81ffdcfc8675bcd9a8505b1a11ffb271
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/25/2020
ms.locfileid: "82158486"
---
# <a name="core-net-libraries-breaking-changes"></a><span data-ttu-id="1f137-103">Podstawowe zmiany w bibliotekach .NET</span><span class="sxs-lookup"><span data-stu-id="1f137-103">Core .NET libraries breaking changes</span></span>

<span data-ttu-id="1f137-104">Podstawowe biblioteki .NET zapewniają pierwotne i inne typy ogólne używane przez platformę .NET Core.</span><span class="sxs-lookup"><span data-stu-id="1f137-104">The core .NET libraries provide the primitives and other general types used by .NET Core.</span></span>

<span data-ttu-id="1f137-105">Następujące istotne zmiany zostały udokumentowane na tej stronie:</span><span class="sxs-lookup"><span data-stu-id="1f137-105">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="1f137-106">Zmiana podziału</span><span class="sxs-lookup"><span data-stu-id="1f137-106">Breaking change</span></span> | <span data-ttu-id="1f137-107">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="1f137-107">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="1f137-108">Interfejsy API służące do raportowania wersji teraz produktu i nie wersji</span><span class="sxs-lookup"><span data-stu-id="1f137-108">APIs that report version now report product and not file version</span></span>](#apis-that-report-version-now-report-product-and-not-file-version) | <span data-ttu-id="1f137-109">3.0</span><span class="sxs-lookup"><span data-stu-id="1f137-109">3.0</span></span> |
| [<span data-ttu-id="1f137-110">Niestandardowe wystąpienia EncoderFallbackBuffer nie mogą podlegać rekursywnie</span><span class="sxs-lookup"><span data-stu-id="1f137-110">Custom EncoderFallbackBuffer instances cannot fall back recursively</span></span>](#custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively) | <span data-ttu-id="1f137-111">3.0</span><span class="sxs-lookup"><span data-stu-id="1f137-111">3.0</span></span> |
| [<span data-ttu-id="1f137-112">Zmiany zachowań formatowania zmiennoprzecinkowego i analizowania</span><span class="sxs-lookup"><span data-stu-id="1f137-112">Floating point formatting and parsing behavior changes</span></span>](#floating-point-formatting-and-parsing-behavior-changed) | <span data-ttu-id="1f137-113">3.0</span><span class="sxs-lookup"><span data-stu-id="1f137-113">3.0</span></span> |
| [<span data-ttu-id="1f137-114">Operacje analizowania zmiennoprzecinkowe nie będą już kończyć się niepowodzeniem lub nie generują wyjątku overflow</span><span class="sxs-lookup"><span data-stu-id="1f137-114">Floating-point parsing operations no longer fail or throw an OverflowException</span></span>](#floating-point-parsing-operations-no-longer-fail-or-throw-an-overflowexception) | <span data-ttu-id="1f137-115">3.0</span><span class="sxs-lookup"><span data-stu-id="1f137-115">3.0</span></span> |
| [<span data-ttu-id="1f137-116">InvalidAsynchronousStateException — przeniesiony do innego zestawu</span><span class="sxs-lookup"><span data-stu-id="1f137-116">InvalidAsynchronousStateException moved to another assembly</span></span>](#invalidasynchronousstateexception-moved-to-another-assembly) | <span data-ttu-id="1f137-117">3.0</span><span class="sxs-lookup"><span data-stu-id="1f137-117">3.0</span></span> |
| [<span data-ttu-id="1f137-118">Zastępowanie źle sformułowanych sekwencji bajtów w formacie UTF-8 następuje po wskazówkach dotyczących standardu Unicode</span><span class="sxs-lookup"><span data-stu-id="1f137-118">Replacing ill-formed UTF-8 byte sequences follows Unicode guidelines</span></span>](#replacing-ill-formed-utf-8-byte-sequences-follows-unicode-guidelines) | <span data-ttu-id="1f137-119">3.0</span><span class="sxs-lookup"><span data-stu-id="1f137-119">3.0</span></span> |
| [<span data-ttu-id="1f137-120">TypeDescriptionProviderAttribute przeniesiony do innego zestawu</span><span class="sxs-lookup"><span data-stu-id="1f137-120">TypeDescriptionProviderAttribute moved to another assembly</span></span>](#typedescriptionproviderattribute-moved-to-another-assembly) | <span data-ttu-id="1f137-121">3.0</span><span class="sxs-lookup"><span data-stu-id="1f137-121">3.0</span></span> |
| [<span data-ttu-id="1f137-122">Element ZipArchiveEntry nie obsługuje już archiwów z niespójnymi rozmiarami wpisów</span><span class="sxs-lookup"><span data-stu-id="1f137-122">ZipArchiveEntry no longer handles archives with inconsistent entry sizes</span></span>](#ziparchiveentry-no-longer-handles-archives-with-inconsistent-entry-sizes) | <span data-ttu-id="1f137-123">3.0</span><span class="sxs-lookup"><span data-stu-id="1f137-123">3.0</span></span> |
| [<span data-ttu-id="1f137-124">Typ wyjątku serializatora JSON został zmieniony z elementu Jsonexception na NotSupportedException</span><span class="sxs-lookup"><span data-stu-id="1f137-124">JSON serializer exception type changed from JsonException to NotSupportedException</span></span>](#json-serializer-exception-type-changed-from-jsonexception-to-notsupportedexception) | <span data-ttu-id="1f137-125">3.0</span><span class="sxs-lookup"><span data-stu-id="1f137-125">3.0</span></span> |
| [<span data-ttu-id="1f137-126">Zmień semantykę (String) na wartość null w Utf8JsonWriter</span><span class="sxs-lookup"><span data-stu-id="1f137-126">Change in semantics of (string)null in Utf8JsonWriter</span></span>](#change-in-semantics-of-stringnull-in-utf8jsonwriter) | <span data-ttu-id="1f137-127">3.0</span><span class="sxs-lookup"><span data-stu-id="1f137-127">3.0</span></span> |
| [<span data-ttu-id="1f137-128">Metody JsonEncodedText. Encode mają dodatkowy argument JavaScriptEncoder</span><span class="sxs-lookup"><span data-stu-id="1f137-128">JsonEncodedText.Encode methods have an additional JavaScriptEncoder argument</span></span>](#jsonencodedtextencode-methods-have-an-additional-javascriptencoder-argument) | <span data-ttu-id="1f137-129">3.0</span><span class="sxs-lookup"><span data-stu-id="1f137-129">3.0</span></span> |
| [<span data-ttu-id="1f137-130">Zmieniono sygnaturę JsonFactoryConverter. isconverter</span><span class="sxs-lookup"><span data-stu-id="1f137-130">JsonFactoryConverter.CreateConverter signature changed</span></span>](#jsonfactoryconvertercreateconverter-signature-changed) | <span data-ttu-id="1f137-131">3.0</span><span class="sxs-lookup"><span data-stu-id="1f137-131">3.0</span></span> |
| [<span data-ttu-id="1f137-132">Zmiany interfejsu API jsonelement</span><span class="sxs-lookup"><span data-stu-id="1f137-132">JsonElement API changes</span></span>](#jsonelement-api-changes) | <span data-ttu-id="1f137-133">3.0</span><span class="sxs-lookup"><span data-stu-id="1f137-133">3.0</span></span> |
| [<span data-ttu-id="1f137-134">Element FieldInfo. SetValue zgłasza wyjątek dla pól static, tylko init</span><span class="sxs-lookup"><span data-stu-id="1f137-134">FieldInfo.SetValue throws exception for static, init-only fields</span></span>](#fieldinfosetvalue-throws-exception-for-static-init-only-fields) | <span data-ttu-id="1f137-135">3.0</span><span class="sxs-lookup"><span data-stu-id="1f137-135">3.0</span></span> |
| [<span data-ttu-id="1f137-136">Pola prywatne dodane do wbudowanych typów struktur</span><span class="sxs-lookup"><span data-stu-id="1f137-136">Private fields added to built-in struct types</span></span>](#private-fields-added-to-built-in-struct-types) | <span data-ttu-id="1f137-137">2.1</span><span class="sxs-lookup"><span data-stu-id="1f137-137">2.1</span></span> |
| [<span data-ttu-id="1f137-138">Zmień wartość domyślną UseShellExecute</span><span class="sxs-lookup"><span data-stu-id="1f137-138">Change in default value of UseShellExecute</span></span>](#change-in-default-value-of-useshellexecute) | <span data-ttu-id="1f137-139">2.1</span><span class="sxs-lookup"><span data-stu-id="1f137-139">2.1</span></span> |
| [<span data-ttu-id="1f137-140">Wersje OpenSSL na macOS</span><span class="sxs-lookup"><span data-stu-id="1f137-140">OpenSSL versions on macOS</span></span>](#openssl-versions-on-macos) | <span data-ttu-id="1f137-141">2.1</span><span class="sxs-lookup"><span data-stu-id="1f137-141">2.1</span></span> |
| [<span data-ttu-id="1f137-142">UnauthorizedAccessException zgłoszone przez FileSystemInfo. Attributes</span><span class="sxs-lookup"><span data-stu-id="1f137-142">UnauthorizedAccessException thrown by FileSystemInfo.Attributes</span></span>](#unauthorizedaccessexception-thrown-by-filesysteminfoattributes) | <span data-ttu-id="1f137-143">1.0</span><span class="sxs-lookup"><span data-stu-id="1f137-143">1.0</span></span> |
| [<span data-ttu-id="1f137-144">Obsługa wyjątków uszkodzonego stanu procesu nie jest obsługiwana</span><span class="sxs-lookup"><span data-stu-id="1f137-144">Handling corrupted-process-state exceptions is not supported</span></span>](#handling-corrupted-state-exceptions-is-not-supported) | <span data-ttu-id="1f137-145">1.0</span><span class="sxs-lookup"><span data-stu-id="1f137-145">1.0</span></span> |

## <a name="net-core-30"></a><span data-ttu-id="1f137-146">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="1f137-146">.NET Core 3.0</span></span>

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

## <a name="net-core-21"></a><span data-ttu-id="1f137-147">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="1f137-147">.NET Core 2.1</span></span>

[!INCLUDE[Private fields added to built-in struct types](~/includes/core-changes/corefx/2.1/instantiate-struct.md)]

***

[!INCLUDE[Change in default value of UseShellExecute](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

***

[!INCLUDE [OpenSSL versions on macOS](../../../includes/core-changes/corefx/openssl-dependencies-macos.md)]

***

## <a name="net-core-10"></a><span data-ttu-id="1f137-148">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="1f137-148">.NET Core 1.0</span></span>

[!INCLUDE [UnauthorizedAccessException thrown by FileSystemInfo.Attributes](~/includes/core-changes/corefx/1.0/filesysteminfo-attributes-exceptions.md)]

***

[!INCLUDE [corrupted-state-exceptions](~/includes/core-changes/corefx/1.0/corrupted-state-exceptions.md)]

***

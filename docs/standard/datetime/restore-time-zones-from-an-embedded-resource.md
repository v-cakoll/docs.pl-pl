---
title: 'Porady: Przywracanie stref czasowych z zasobu osadzonego'
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], deserializing
- time zones [.NET Framework], restoring
ms.assetid: 6b7b4de9-da07-47e3-8f4c-823f81798ee7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 31dd785c419d9a8e11eb23deabd2dfa71c4d6e9c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33572349"
---
# <a name="how-to-restore-time-zones-from-an-embedded-resource"></a><span data-ttu-id="4bc0c-102">Porady: Przywracanie stref czasowych z zasobu osadzonego</span><span class="sxs-lookup"><span data-stu-id="4bc0c-102">How to: Restore time zones from an embedded resource</span></span>

<span data-ttu-id="4bc0c-103">W tym temacie opisano sposób Przywracanie stref czasowych, które zostały zapisane w pliku zasobów.</span><span class="sxs-lookup"><span data-stu-id="4bc0c-103">This topic describes how to restore time zones that have been saved in a resource file.</span></span> <span data-ttu-id="4bc0c-104">Aby uzyskać informacje i instrukcje dotyczące zapisywanie stref czasowych, zobacz [porady: zapisywanie stref czasowych w zasobie osadzonym](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md).</span><span class="sxs-lookup"><span data-stu-id="4bc0c-104">For information and instructions about saving time zones, see [How to: Save time zones to an embedded resource](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md).</span></span>

### <a name="to-deserialize-a-timezoneinfo-object-from-an-embedded-resource"></a><span data-ttu-id="4bc0c-105">Do deserializacji obiektów TimeZoneInfo z zasobu osadzonego</span><span class="sxs-lookup"><span data-stu-id="4bc0c-105">To deserialize a TimeZoneInfo object from an embedded resource</span></span>

1. <span data-ttu-id="4bc0c-106">Jeśli strefa czasowa do pobrania nie jest niestandardowa strefa czasowa, spróbuj utworzyć przy użyciu <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="4bc0c-106">If the time zone to be retrieved is not a custom time zone, try to instantiate it by using the <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> method.</span></span>

2. <span data-ttu-id="4bc0c-107">Utwórz wystąpienie <xref:System.Resources.ResourceManager> obiektu przez przekazanie w pełni kwalifikowana nazwa pliku zasobu osadzonego i odwołanie do zestawu, który zawiera plik zasobu.</span><span class="sxs-lookup"><span data-stu-id="4bc0c-107">Instantiate a <xref:System.Resources.ResourceManager> object by passing the fully qualified name of the embedded resource file and a reference to the assembly that contains the resource file.</span></span>

   <span data-ttu-id="4bc0c-108">Jeśli nie można określić pełną nazwę pliku zasobu osadzonego, użyj [Ildasm.exe (dezasembler IL)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) do sprawdzenia manifest zestawu.</span><span class="sxs-lookup"><span data-stu-id="4bc0c-108">If you cannot determine the fully qualified name of the embedded resource file, use the [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) to examine the assembly's manifest.</span></span> <span data-ttu-id="4bc0c-109">`.mresource` Wpis identyfikuje zasób.</span><span class="sxs-lookup"><span data-stu-id="4bc0c-109">An `.mresource` entry identifies the resource.</span></span> <span data-ttu-id="4bc0c-110">W tym przykładzie jest pełna nazwa zasobu `SerializeTimeZoneData.SerializedTimeZones`.</span><span class="sxs-lookup"><span data-stu-id="4bc0c-110">In the example, the resource's fully qualified name is `SerializeTimeZoneData.SerializedTimeZones`.</span></span>

   <span data-ttu-id="4bc0c-111">Jeśli plik zasobu jest osadzony w skład zestawu zawierającego kod wystąpienia strefy czasowej, możesz pobrać odwołanie do niej przez wywołanie metody `static` (`Shared` w języku Visual Basic) <xref:System.Reflection.Assembly.GetExecutingAssembly%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="4bc0c-111">If the resource file is embedded in the same assembly that contains the time zone instantiation code, you can retrieve a reference to it by calling the `static` (`Shared` in Visual Basic) <xref:System.Reflection.Assembly.GetExecutingAssembly%2A> method.</span></span>

3. <span data-ttu-id="4bc0c-112">Jeśli wywołanie <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> metoda kończy się niepowodzeniem, lub jeśli niestandardowa strefa czasowa można utworzyć wystąpienia, należy pobrać ciąg, który zawiera seryjnych strefy czasowej przez wywołanie metody <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="4bc0c-112">If the call to the <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> method fails, or if a custom time zone is to be instantiated, retrieve a string that contains the serialized time zone by calling the <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType> method.</span></span>

4. <span data-ttu-id="4bc0c-113">Deserializacja danych przez strefy czasowej przez wywołanie metody <xref:System.TimeZoneInfo.FromSerializedString%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="4bc0c-113">Deserialize the time zone data by calling the <xref:System.TimeZoneInfo.FromSerializedString%2A> method.</span></span>

## <a name="example"></a><span data-ttu-id="4bc0c-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="4bc0c-114">Example</span></span>

<span data-ttu-id="4bc0c-115">Poniższy przykład deserializuje <xref:System.TimeZoneInfo> obiektu przechowywanego w pliku osadzonego zasobu .NET XML.</span><span class="sxs-lookup"><span data-stu-id="4bc0c-115">The following example deserializes a <xref:System.TimeZoneInfo> object stored in an embedded .NET XML resource file.</span></span>

[!code-csharp[TimeZone2.Serialization#3](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#3)]
[!code-vb[TimeZone2.Serialization#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#3)]

<span data-ttu-id="4bc0c-116">Ten kod ilustruje obsługi wyjątków, aby upewnić się, że <xref:System.TimeZoneInfo> występuje obiektu wymagane przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="4bc0c-116">This code illustrates exception handling to ensure that a <xref:System.TimeZoneInfo> object required by the application is present.</span></span> <span data-ttu-id="4bc0c-117">Najpierw próbuje utworzyć wystąpienia <xref:System.TimeZoneInfo> obiektu, pobierając go z rejestru przy użyciu <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="4bc0c-117">It first tries to instantiate a <xref:System.TimeZoneInfo> object by retrieving it from the registry using the <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> method.</span></span> <span data-ttu-id="4bc0c-118">Jeśli nie można utworzyć wystąpienia strefy czasowej, kod pobiera z pliku zasobu osadzonego.</span><span class="sxs-lookup"><span data-stu-id="4bc0c-118">If the time zone cannot be instantiated, the code retrieves it from the embedded resource file.</span></span>

<span data-ttu-id="4bc0c-119">Ponieważ dane dla niestandardowych stref czasowych (utworzone przy użyciu stref czasowych <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> — metoda) nie są przechowywane w rejestrze, kod nie wywołuje <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> można utworzyć wystąpienia strefę czasową dla Palmer, Antarktyka.</span><span class="sxs-lookup"><span data-stu-id="4bc0c-119">Because data for custom time zones (time zones instantiated by using the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method) are not stored in the registry, the code does not call the <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> to instantiate the time zone for Palmer, Antarctica.</span></span> <span data-ttu-id="4bc0c-120">Zamiast tego natychmiast wygląda na to do pliku osadzonego zasobu, by pobrać ciąg zawierający dane strefy czasowej, przed wywołaniem <xref:System.TimeZoneInfo.FromSerializedString%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="4bc0c-120">Instead, it immediately looks to the embedded resource file to retrieve a string that contains the time zone's data before it calls the <xref:System.TimeZoneInfo.FromSerializedString%2A> method.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="4bc0c-121">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="4bc0c-121">Compiling the code</span></span>

<span data-ttu-id="4bc0c-122">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="4bc0c-122">This example requires:</span></span>

* <span data-ttu-id="4bc0c-123">Odwołanie do System.Windows.Forms.dll i System.Core.dll dodania do projektu.</span><span class="sxs-lookup"><span data-stu-id="4bc0c-123">That a reference to System.Windows.Forms.dll and System.Core.dll be added to the project.</span></span>

* <span data-ttu-id="4bc0c-124">Czy następujących przestrzeni nazw można importować:</span><span class="sxs-lookup"><span data-stu-id="4bc0c-124">That the following namespaces be imported:</span></span>

  [!code-csharp[TimeZone2.Serialization#2](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#2)]
  [!code-vb[TimeZone2.Serialization#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#2)]

## <a name="see-also"></a><span data-ttu-id="4bc0c-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4bc0c-125">See also</span></span>

<span data-ttu-id="4bc0c-126">[Daty, godziny i strefy czasowe](../../../docs/standard/datetime/index.md)
[Przegląd stref czasowych](../../../docs/standard/datetime/time-zone-overview.md)
[porady: zapisywanie stref czasowych w zasobie osadzonym](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md)</span><span class="sxs-lookup"><span data-stu-id="4bc0c-126">[Dates, times, and time zones](../../../docs/standard/datetime/index.md)
[Time zone overview](../../../docs/standard/datetime/time-zone-overview.md)
[How to: Save time zones to an embedded resource](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md)</span></span>

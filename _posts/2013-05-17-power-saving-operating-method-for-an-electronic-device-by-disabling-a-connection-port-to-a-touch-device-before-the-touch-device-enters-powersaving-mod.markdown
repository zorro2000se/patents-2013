---

title: Power saving operating method for an electronic device by disabling a connection port to a touch device before the touch device enters power-saving mode
abstract: A power-saving operating method for an electronic device is provided. A control chip of the electronic device has an interrupt pin, and the electronic device couples to a touch device through a connection port and the interrupt pin. When the touch device is idle for over an idle time, a BIOS is informed through the interrupt pin to disable the connection port. When a number of touch signals received from the touch device within a first predetermined time is not less than a first predetermined amount, the connection port is enabled. When the number of the touch signals received from the touch device within the first predetermined time is less than the first predetermined amount or none of the touch signal is received within the first predetermined time, a reading operation for reading the connection port is interrupted and the touch device enters a power-saving mode.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=09207742&OS=09207742&RS=09207742
owner: Wistron Corporation
number: 09207742
owner_city: New Taipei
owner_country: TW
publication_date: 20130517
---
This application claims the priority benefit of Taiwan application serial no. 102102992 filed on Jan. 25 2013. The entirety of the above mentioned patent application is hereby incorporated by reference herein and made a part of this specification.

The invention relates to an operating method and an electronic device and more particularly to a power saving operating method for a touch device and an electronic device using the same.

Power management is one of the most important topics for common desktop computers as well as portable peripheral equipments such as notebook computer which relies on power supplied by batteries. A crucial key for power management is to effectively reduce power usage of inactive equipments with respect to operating conditions of computer devices and peripheral equipments so as to improve efficiency and extend lifetime of batteries.

Conventional computers generally adopt an advanced power management APM specification such specification is an application programming interface developed by Microsoft and Intel for monitors which can be used to store a power supply setting between personal computers and monitors having specific batteries. A major concern to the APM lies where it is mainly controlled by a firmware of a basic input output System BIOS and power may not be effectively utilized with changes in operating processes. The APM may only guess current activities of a user based on interrupt request IRQ and input output port I O Port . Therefore it is difficult to meet all requirements in effectively saving power and extending lifetime of batteries.

In order to maintain a common power management interface between operating systems and hardware an advanced configuration and power interface ACPI standard has been developed to improve efficiency of power management based on interactions between the user and the operating system by managing power in response to commands from an operating system instead of the BIOS. That is once the operating system is informed of certain functions in the computer being inactive the functions may be automatically terminated to reduce power consumption. The ACPI interface may providing a proper power and a host working frequency according information such as motherboard temperature fan speed and voltage of the power supply detected by specific hardware so as to effectively distribute and transmit power to system devices thereby achieving power saving while maintaining working efficiency.

Under the power management of ACPI most of devices not being operated under a working condition may enter a sleep state D1 to D3 states which is relatively with less power consumption so as to reduce power consumption. However in order to support a wake function the devices merely reduce power consumption rather than turn off power entirely. A total power consumption to the devices in above said condition may also be a burden that affects lifetime of the battery. Therefore overall lifetime of the battery may be further extended by saving power consumption in the condition.

The invention is directed to a power saving operating method and an electronic device which can reduce power consumption of a touch device when the touch device is idle.

The invention provides a power saving operating method for an electronic device having a processor a control chip and a connection port. The control chip further includes an interrupt pin the electronic device couples to a touch device through the connection port and the interrupt pin and the control chip couples to the connection port. The method includes informing a basic input output system through the interrupt pin of the control chip by the touch device to disable the connection port when the touch device is idle for over an idle time determining whether the processor receives at least one touch signal from the touch device within a first predetermined time enabling the connection port when a number of the at least one touch signal from the touch device received by the processor within the first predetermined time is not less than a first predetermined amount and interrupting a reading operation for reading the connection port and making the touch device enter a power saving mode when the number of the at least touch signal from the touch device received by the processor within the first predetermined time is less than the first predetermined amount or none of the at least signal is received within the first predetermined time.

According to the power saving operating method in an embodiment of the invention the step of informing a basic input output system through the interrupt pin of the control chip by the touch device to disable the connection port when the touch device is idle for over an idle time further includes transmitting an interrupt signal from the touch device to the processor through the interrupt pin of the control chip and disabling the connection port by the BIOS according to the interrupt signal received by the processor.

According to the power saving operating method in an embodiment of the invention the processor executes an operating system and the step of disabling the connection port by the BIOS includes calling an advanced configuration and power interface source language of the basic input output system by an advanced configuration and power interface driver of the operating system according to the interrupt signal received by the processor to make the basic input output system disable the connection port.

According to the power saving operating method in an embodiment of the invention after the step of making the touch device enter the power saving mode the power saving operating method further includes receiving a wake up signal switching the touch device from the power saving mode back to an normal operating mode according to the wake up signal informing the basic input output system through the interrupt pin of the control chip by the touch device to enable the connection port determining whether the processor receives the at least one touch signal from the touch device within a second predetermined time disabling the connection port by the processor when the number of the at least one touch signal from the touch device received by the processor within the second predetermined time is less than a second predetermined amount or none of the at least one touch signal is received within the second predetermined time and re executing the reading operation on the connection port by the processor and writing a data input by the touch device by the processor when the number of the at least touch signal from the touch device received by the processor within the second predetermined time is not less than the second predetermined amount.

According to the power saving operating method in an embodiment of the invention the control chip includes a platform controller hub.

According to the power saving operating method in an embodiment of the invention the interrupt pin includes a general purpose I O.

The invention provides an electronic device having a connection port a control chip a memory unit and a processor. The connection port is coupled to a touch device. The control chip has an interrupt pin the electronic device couples to a touch device through the connection port and the interrupt pin and the control chip couples to the connection port. The memory unit stores a basic input out system BIOS . The touch device transmits an interrupt signal to the processor through the interrupt pin of the control chip when the touch device is idle for over an idle time and the processor executes the basic input output system to disable the connection port according to the received interrupt signal. Whether at least one touch signal from the touch device is received within a first predetermined time is then determined. The BIOS is executed to enable the connection port when a number of the at least one touch signal from the touch device received within the first predetermined is not less than a first predetermined amount. A reading operation for reading the connection port is interrupted and the touch device enters a power saving mode when the number of at least one touch signal from the touch device received within the first predetermined time is less than the first predetermined amount or none of the at least one signal is received within the first predetermined time.

According to the electronic device in an embodiment of the invention the processor executing the basic input output system to disable the connection port further includes calling an advanced configuration and power interface source language of the basic input output system by an advanced configuration and power interface driver of an operating system executed by the processor according to the interrupt signal received by the processor to make the basic input output system disable the connection port.

According to the electronic device in an embodiment of the invention after the touch device enters the power saving mode the electronic device further includes the touch device is switched from the power saving mode back to an normal operating mode according to the wake up signal a resuming signal is transmitted from the touch device to the processor through the interrupt pin of the control chip and the BIOS is executed by the processor to enable the connection port according to the resuming signal determining whether the at least one touch signal from the touch device is received within a second predetermined time by the processor disabling the connection port by the processor when a number of the at least touch signal received from the touch device within the second predetermined time is less than a second predetermined amount or none of the at least one touch signal is received within the second predetermined time and re executing the reading operation on the connection port and writing a data input by the touch device by the processor when the number of the at least one touch signal received from the touch device within the second predetermined time is not less than the second predetermined amount.

According to the electronic device in an embodiment of the invention the control chip includes a platform controller hub.

According to the electronic device in an embodiment of the invention the interrupt pin includes a general purpose I O.

Accordingly the invention provides the interrupt pin on the control chip to be used as a bridge for transmitting control signals between the electronic device and the touch device. When the touch device is idle the interrupt signal is transmitted to the processor through the interrupt pin and with the operating system executed by the processor under the ACPI standard the BIOS is triggered to disable the connection port between the touch device and the electronic device so as to switch the power state of the touch device from the normal operating mode to the power saving mode thereby reducing power consumption of the touch device.

To make the above features and advantages of the invention more comprehensible several embodiments accompanied with drawings are described in detail as follows.

Further the processor can be for example a central processing unit CPU for executing data of hardware firmware and processing software in the electronic device . The control chip can be for example a platform controller hub PCH and uses the interrupt pin such as a general purpose input output general purpose I O GPIO as a bridge for transmitting control signals between the control chip and the touch device . In addition the connection port can be used to transmit data signals between the control chip and the touch device . The touch device can be for example integrated with a display as a touch panel. In addition the memory unit can be for example a random access memory RAM configured to store a basic input output system BIOS . More specifically when the electronic device is powered on the BIOS is loaded not illustrated into the memory unit by a BIOS chip as for the processor to read and execute a booting process. Moreover the BIOS can be for example a BIOS that is complied with an advanced configuration and power interface ACPI standard.

Referring to and together in step S when the touch device is idle for over an idle time a firmware of the touch device informs the BIOS through the interrupt pin of the control chip to disable the connection port . In other words within the idle time e.g. three minutes if a user fails to performed an input operation by using an input device on the touch device as for the touch device to generate a corresponding input signal or transmit any data e.g. when the user uses other input devices instead of the touch device or when the user uses display function of the touch device for a long time without performing input operation directly to the touch device the BIOS is informed through the interrupt pin of the control chip to disable the connection port . The aforementioned idle time can be customized by the user and the invention is not limited thereto.

Next in step S whether the processor receives at least one touch signal from the touch device through the interrupt pin of the control chip within a first predetermined time is determined. In other words a foolproof test is performed after the connection port is disabled and before a power state of the touch device is switched to a power saving mode so as to ensure that the power state of the touch device is not switched between a normal mode D0 and power saving modes D1 to D3 without stopping due to a mistouched input by the user. For instance after the connection port is disabled and before the power state of the touch device is switched to the power saving mode the electronic device holds for a pending time i.e. a first predetermined time such as 110 to 300 seconds . When a number of touch signal from the touch device received by the processor through the interrupt pin of the control chip is not less than a specific amount i.e. a first predetermined amount such as three times within the pending time That is a number of times for the touch device being continuously touched by the user is not less than the specific amount a touch operation constantly performed by the user is determined to be a valid input operation. Otherwise the touch operation by the user is determined to be an invalid input operation i.e. the mistouched input .

In step S the connection port is enabled when the number of at least one touch signal from the touch device received by the processor through the interrupt pin of the control chip within a first predetermined time is not less than a first predetermined amount. On the other hand in step S a reading operation for reading the connection port is interrupted and the touch device enters a power saving mode when the number of the at least one touch signal from the touch device received by the processor through the interrupt pin of the control chip within the first predetermined time is less than the first predetermined amount or none of the at least one touch signal is received within the first predetermined time.

Next in step S whether the processor receives the at least one touch signal from the touch device through the interrupt pin of the control chip within a second predetermined time is determined. That is another foolproof test is performed to ensure that the connection port is enabled when the valid input operation is performed to the touch device so that the processor may perform the reading operation on the connection port and writes data input by the touch device. For instance after the connection port is enabled and read the electronic device holds for a pending time i.e. a second predetermined time such as 110 to 300 seconds . When a number of touch signal from the touch device received by the processor is not less than a specific amount i.e. a second predetermined amount such as three times within the pending time meaning that a number of times for the touch device being continuously touched by the user is not less than the specific number of times such a touch operation constantly performed by the user is determined to be a valid input operation. Otherwise the touch operation by the user is determined to be an invalid input operation i.e. the mistouched input .

In step S the processor re executes the reading operation on the connection port and writes a data input by the touch device when the number of the at least one touch signal from the touch device received within the second predetermined time is not less than the second predetermined amount. Otherwise in step S the processor disables the connection port when the number of the at least one touch signal from the touch device received within the second predetermined time is less than a second predetermined amount or none of the at least one touch signal is received within the second predetermined time.

Altogether in the invention the interrupt pin on the control chip is used as a bridge medium for transmitting control signals between the electronic device and the touch device. When the touch device is idle the interrupt signal is transmitted to the processor through the interrupt pin and with the operating system executed by the processor under the ACPI standard the BIOS is triggered to disable the connection port between the touch device and the electronic device so as to switch the power state of the touch device from the normal operating mode to the power saving mode. Therefore the power consumption of the touch device is reduced.

Although the present invention has been described with reference to the above embodiments it will be apparent to one of ordinary skill in the art that modifications to the described embodiments may be made without departing from the spirit of the invention. Accordingly the scope of the invention will be defined by the attached claims and not by the above detailed descriptions.


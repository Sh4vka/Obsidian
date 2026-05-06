`interface/stlink` - подключение с помощью stlink (swd)
`target/stm32fx.cfg` - цель чип stm32f1 
Находят по vid (vendor id) и pid(product id)

**Наши драйвера**
 `openocd -c "adapter driver *name*; *name* *port*; adapter speed *kHz* -f *цель*`
 
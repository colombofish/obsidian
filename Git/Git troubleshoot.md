*Note: I am using older version and don't have ed_25519 file in the ./ssh folder. Instead I have id_rsa. So to add ssh agent do the following. Else, upgrade OpenSSH to newer ver, which supports ed_.. file*
`eval 'ssh-agent -s'`
`ssh-add id_rsa` //private file. Then add the passphrase 'maiden name'
`cat ~/.ssh/id_rsa.pub | clip` // copies the content of id_rsa.pub into the clipboard ex: below
ssh-rsa `AAAAB3NzaC1yc2EAAAADAQABAAACAQCvuv1YyDrQ2a8qTsURKrA4NUs/rRhlD90v/LB4ikgCL8nlq+b/sULJwG5eZJxUwdZVtDoSZSzXg0t0lr27oSDCCbt8dkYtb2BYLqC8ihrf7O09zHb6ik3ApXVZ99ilONpmFhs41TlAu57s+5VZc1/kH3PLTyCN9RcgEaYoYfAKH1XyxtgwML2wwZXePFF+CA00q9Fbcb+ZaMuROIEHp5ltDI9mHdjrhhXG2gZLE+9JuKfR80pPvfnmhafNHrl0da3D2u2AdnHAVv2h0c92btBBzQLsZ9fPaVGaGAvQoy4SjZOvOv6MzAI5R3iYLq4/yVZiRiU+Fhd0i0IEKP3hWSouCJ3St0Fi1/lP8QYvt/c0BJZC9sVjFz6ZQ3tR5Vg6QBc2bzozUM/ep4rveST4lEh30rlE9BMaY74z+/fWRRDG12UXHZk0dRDFu+U9IMPWSrE4gypvhIczgVwvYS6niDa1Y2abeo6JHxWLWjdV7gt1N25mWvil8zIhhSsz7Jr0Z2W6TOKmuYC/nqO3c6dLR+GQwIu6H7xZFgjtY/15U8q+Eh2naCRyur+uUq9aqi7s8zlJBsSUBeevYB1aKWEUaQI46O9UR6u2o42p8cKdIgdn9wCRbndLt5NoRu+4IADYdsCHsumr2s3yYlgDHmRW16Ed2qLdhNU7R2z8bx4kZfSOzw== colombofish@hotmail.com` // add this key to github.com 

`git push -u origin yoursettings` to push to the github.com
provide passphrase to complete the commit

